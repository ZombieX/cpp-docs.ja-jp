---
title: タスクの並列化 (同時実行ランタイム) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec6e99b3e4f1e86d9f0ee42ca92a93a57b1a1fb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378086"
---
# <a name="task-parallelism-concurrency-runtime"></a>タスクの並列化 (同時実行ランタイム)

同時実行ランタイムで、*タスク*は特定のジョブを実行し、通常他のタスクと並列で実行される作業の単位です。 タスクに編成されたより細かな追加のタスクに分解することができます、*タスク グループ*します。

非同期コードを記述して、非同期操作が完了したときに操作を実行する場合に、タスクを使用します。 たとえば、ファイルから非同期的に読み取り、別のタスクを使用してタスクを使用する可能性があります:、*継続タスク*、このドキュメントの後半で説明する — 使用可能になった後にデータを処理します。 逆に、タスク グループを使用して、並列処理を分解することができます。 たとえば、残存作業を 2 つのパーティションに分割する再帰的なアルゴリズムがあるとします。 タスク グループを使用すると、これらのパーティションを同時に実行して、分割処理の完了を待つことができます。

> [!TIP]

>  同じルーチンを並列でのコレクションのすべての要素に適用する場合など、並列アルゴリズムの使用[concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for)、タスクまたはタスク グループ代わりにします。 並列アルゴリズムの詳細については、次を参照してください。[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)します。

## <a name="key-points"></a>主要なポイント

- ラムダ式に変数を渡すときに参照渡しを使用する場合、タスクが終了するまでその変数の有効期間が続くようにする必要があります。

- タスクを使用して、(、 [concurrency::task](../../parallel/concrt/reference/task-class.md)クラス) 非同期コードを記述するとき。 タスク クラスは、同時実行ランタイムではなく、Windows ThreadPool をスケジューラとして使用します。

- タスク グループを使用して、(、 [concurrency::task_group](reference/task-group-class.md)クラスまたは[concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)アルゴリズム) に並列処理に小さい部分に分解し、これら小さなを待機したい場合完了する部分。

- 使用して、 [:then](reference/task-class.md#then) continuation を作成します。 A*継続*は別のタスクが完了した後に非同期的に実行されるタスクです。 一連の非同期処理を形成するために、継続をいくつでも接続できます。

- タスク ベースの継続は、継続元タスクが取り消されたり、例外をスローした場合でも、継続元タスクが完了すると常に実行がスケジュールされます。

- 使用[concurrency::when_all](reference/concurrency-namespace-functions.md#when_all)一連のタスクのすべてのメンバーが完了した後に完了するタスクを作成します。 使用[concurrency::when_any](reference/concurrency-namespace-functions.md#when_any)一連のタスクの 1 つのメンバーが完了した後に完了するタスクを作成します。

- タスクとタスク グループは、並列パターン ライブラリ (PPL) の取り消し機構に参加できます。 詳細については、次を参照してください。 [PPL における取り消し処理](cancellation-in-the-ppl.md)します。

- タスクとタスク グループによってスローされる例外をランタイムが処理する方法については、次を参照してください。[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)します。

## <a name="in-this-document"></a>目次

- [ラムダ式の使用](#lambdas)

- [Task クラス](#task-class)

- [継続タスク](#continuations)

- [値ベースの継続とタスク ベースの継続](#value-versus-task)

- [タスクを構成します。](#composing-tasks)

    - [When_all 関数](#when-all)

    - [When_any 関数](#when-any)

- [遅延したタスクの実行](#delayed-tasks)

- [タスク グループ](#task-groups)

- [Task_group structured_task_group の違いを比較します。](#comparing-groups)

- [例](#example)

- [信頼性の高いプログラミング](#robust)

##  <a name="lambdas"></a> ラムダ式の使用

ラムダ式は簡潔な構文であるため、タスクおよびタスク グループで実行される作業を定義する一般的な方法です。 使用のヒントを次に示します。

- 通常、タスクはバックグラウンド スレッドで実行されるため、ラムダ式の変数をキャプチャする場合にはオブジェクトの有効期間に注意してください。 変数を値でキャプチャすると、その変数のコピーがラムダの本体に作成されます。 参照によってキャプチャする場合には、コピーは作成されません。 したがって、参照によってキャプチャするすべての変数の有効期間が、それを使用するタスクのために十分であるように注意します。

- タスクにラムダ式を渡す場合、スタックに割り当てられた変数を参照によってキャプチャしないようにします。

- ラムダ式でキャプチャする変数を明示して、値でのキャプチャと参照でのキャプチャを識別できるようにします。 このため、ラムダ式に対して `[=]` または `[&]` オプションを使用しないことをお勧めします。

一般的なパターンは、継続のチェーンの 1 つのタスクが変数に割り当てられ、別のタスクがその変数を読み取る場合です。 各継続タスクが変数のそれぞれのコピーを保持するため、値によるキャプチャができません。 スタック割り当て変数においても、変数が有効でなくなる場合があるため、参照によるキャプチャができません。

この問題を解決するには、スマート ポインターの場合をなど、使用[std::shared_ptr](../../standard-library/shared-ptr-class.md)変数をラップすると、スマート ポインターを値渡し。 この方法を使用すると、基になるオブジェクトが割り当てられ、読み込むことができ、それを使用するタスクのために十分な有効期間となります。 変数が Windows ランタイム オブジェクトへのポインターであったり、参照カウント ハンドル (`^`) である場合でも、この方法を使用できます。 基本的な例は次のとおりです。

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

ラムダ式について詳しくは、「[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)」をご覧ください。

##  <a name="task-class"></a> Task クラス

使用することができます、 [concurrency::task](../../parallel/concrt/reference/task-class.md)クラスに依存する操作の一連のタスクを構成します。 このコンポジション モデルの概念ではサポートされて*継続*します。 ときに実行されるコードを継続できるように、前または*継続元*タスクが完了します。 継続元タスクの結果は、1 つ以上の継続タスクへの入力として渡されます。 継続元タスクが完了すると、それを待っているすべての継続タスクが実行のためにスケジュールされます。 各継続タスクは継続元タスクの結果のコピーを受信します。 また、これらの継続タスクが、他の継続の継続元タスクである場合もあり、このようにしてタスクのチェーンが作成されます。 継続を使うと、特定の依存関係を持つ、任意の長さのタスクのチェーンを作成できます。 また、タスクは開始前または実行中に協調的に、取り消しに参加できます。 この取り消しモデルの詳細については、次を参照してください。 [PPL における取り消し処理](cancellation-in-the-ppl.md)します。

`task` はテンプレート クラスです。 型パラメーター `T` は、タスクで生成される結果の型です。 タスクが値を返さない場合には、この型は `void` となります。 `T` は `const` 修飾子を使用できません。

指定したタスクを作成するときに、*処理関数*タスクの本体を実行します。 この処理関数には、ラムダ関数、関数ポインター、または関数オブジェクトを使用できます。 タスクの結果を取得することがなく完了を待機する呼び出し、 [::wait](reference/task-class.md#wait)メソッド。 `task::wait`メソッドを返します。 を[concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status)タスクが完了またはキャンセルされたかどうかを示す値。 タスクの結果を取得する、 [::task_canceled](reference/task-class.md#get)メソッド。 このメソッドは、`task::wait` を呼び出してタスクの完了を待ち、結果が使用できるようになるまで現在のスレッドの実行をブロックします。

次の例では、タスクを作成し、結果を待って、値を表示する方法を示します。 このドキュメントの例では、より簡潔な構文を提供するため、ラムダ関数を使用しています。 しかし、タスクを使用する場合には、関数ポインター、および関数オブジェクトを使用することも可能です。

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

使用すると、 [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task)関数を使用できます、`auto`キーワード、型を宣言する代わりにします。 たとえば、単位行列を作成して印刷する、次のコードを考えてみます。

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

`create_task` 関数を使用して同等の操作を行うことができます。

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

タスクの実行時に例外がスローされた場合、ランタイムは、それ以降の `task::get` または `task::wait` の呼び出し、またはタスク ベースの継続への呼び出しで、その例外をマーシャリングします。 タスク例外処理機構の詳細については、次を参照してください。[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)します。

使用する例については`task`、 [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)、キャンセルを参照してください[チュートリアル: を使用してタスクの接続および XML HTTP 要求](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)します。 (`task_completion_event` クラスについてはドキュメントの後の部分で説明されています。)

> [!TIP]
>  UWP アプリでのタスクに固有の詳細については、次を参照してください。 [C++ での非同期プログラミング](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)と[を作成する非同期操作で C++ UWP アプリの](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)します。

##  <a name="continuations"></a> 継続タスク

非同期プログラミングでは、非同期操作で完了時に 2 番目の操作を呼び出してデータを渡すのが一般的です。 これまで、この処理はコールバック メソッドを使用して行っていました。 によって、同時実行ランタイムで同じ機能が提供される*継続タスク*します。 継続タスクを (だけ継続とも呼ばれます) と呼ばれる別のタスクによって呼び出される非同期タスクは、*継続元*継続元が完了すると、します。 継続を使用して、次の操作を行うことができます。

- 継続元のデータを継続に渡します。

- 継続を呼び出す場合、呼び出さない場合についての正確な条件を指定します。

- 継続が開始される前、または継続の実行中に、継続を取り消します。

- 継続をスケジュールする方法についてのヒントを提供します。 (これはユニバーサル Windows プラットフォーム (UWP) アプリのみに適用されます。 詳細については、次を参照してください[を作成する非同期操作で C++ UWP アプリの](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。)。

- 同じ継続元から複数の継続を呼び出します。

- 複数の継続元のすべてまたはいずれかが完了したときに 1 つの継続を呼び出します。

- 任意の長さで連続して継続を実行します。

- 継続元によってスローされた例外を処理するために継続を使用します。

これらの機能を使うと、最初のタスクが完了したときに、1 つ以上のタスクを実行できます。 たとえば、最初のタスクがディスクからデータを読み取った後に、ファイルを圧縮する継続を作成できます。

次の例を使用する 1 つ前の変更、 [:then](reference/task-class.md#then)メソッドを利用可能になったら、継続元タスクの値を出力する継続をスケジュールします。

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

タスクを任意の長さにチェーンしたり、入れ子にできます。 またタスクは、複数の継続を持つことができます。 次の例では、前のタスクの値を 3 回インクリメントする、基本的な継続のチェーンを示しています。

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

継続は、別のタスクを返すこともできます。 取り消されない場合、このタスクは後続の継続の前に実行されます。 この手法と呼ばれる*非同期ラッピング解除*します。 非同期ラッピング解除は、追加の作業をバックグラウンドで実行するときに、現在のタスクが現在のスレッドをブロックしないようにする場合に役立ちます。 (これは、UWP アプリで共通の継続が UI スレッドで実行できます) です。 次の例は、3 つのタスクを示しています。 最初のタスクは、継続タスクの前に実行される、別のタスクを返します。

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
>  タスクの継続が `N` 型の入れ子のタスクを返す場合、結果のタスクは `N` 型でなく `task<N>` 型となり、入れ子のタスクが完了すると終了します。 つまり、継続は入れ子のタスクのラッピング解除を行います。

##  <a name="value-versus-task"></a> 値ベースの継続とタスク ベースの継続

`task` オブジェクトは戻り値の型が `T` であるため、その継続タスクに `T` または `task<T>` 型の値を指定できます。 型を受け取る継続`T`と呼ばれますが、*値ベースの継続*します。 値ベースの継続は、継続元タスクがエラーなしに完了して取り消されない場合に、実行のためにスケジュールされます。 型を受け取る継続`task<T>`とそのパラメーターが呼ばれるよう、*タスク ベースの継続*します。 タスク ベースの継続は、継続元タスクが取り消されたり、例外をスローした場合でも、継続元タスクが完了すると常に実行がスケジュールされます。 次に `task::get` を呼び出して、継続元タスクの結果を取得できます。 継続元タスクが取り消された場合`task::get`スロー [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md)します。 継続元タスクが例外をスローすると、`task::get` は再度、例外をスローします。 タスク ベースの継続は、その継続元タスクが取り消された場合、取り消し済みとしてマークされません。

##  <a name="composing-tasks"></a> タスクを構成します。

このセクションについて説明します、 [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all)と[concurrency::when_any](reference/concurrency-namespace-functions.md#when_all)一般的なパターンを実装するために複数のタスクを作成する関数は、することができます。

###  <a name="when-all"></a> When_all 関数

`when_all` 関数は、一連のタスクの完了後に完了するタスクを生成します。 返します、std::[ベクター](../../standard-library/vector-class.md)セット内の各タスクの結果を格納するオブジェクト。 次の基本的な例では、`when_all` を使用して、3 つの他のタスクの完了を表すタスクを作成します。

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
>  `when_all` に渡すタスクは均一である必要があります。 つまり、これらはすべて同じ型を返す必要があります。

次に示す例のように、`&&` 構文を使用して、一連のタスクの完了後に完了するタスクを生成することもできます。

`auto t = t1 && t2; // same as when_all`

通常は、継続を `when_all` と共に使用して、一連のタスクが終了した後に操作を実行します。 前の例を変更した次の例では、それぞれが `int` の結果を生成する、3 つのタスクの合計を印刷します。

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

この例では、タスク ベースの継続を作成するために `task<vector<int>>` を指定することもできます。

一連のタスクのいずれかのタスクが取り消されたり、例外をスローした場合、`when_all` は残りのタスクを完了を待たずに、直ちに終了します。 例外がスローされた場合、`task::get` を返すタスク オブジェクトで `task::wait` または `when_all` を呼び出すと、ランタイムは再度、例外をスローします。 複数のタスクからスローすると、ランタイムはその中の 1 つを選択します。 したがって、すべてのタスクが完了してからすべての例外を確認するようにします。タスクの例外がハンドルされない場合、アプリケーションは終了します。

プログラムがすべての例外を確認するために使用できるユーティリティ関数を次に示します。 指定された範囲のタスクごとに、`observe_all_exceptions` は再スローされる例外をトリガーし、その例外を受け取ります。

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

C++ と XAML を使用し、一連のファイルをディスクに書き込んでいる UWP アプリを検討してください。 次の例は、`when_all` と `observe_all_exceptions` を使用して、プログラムがすべての例外を確認する方法を示します。

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>この例を実行するには

1. MainPage.xaml で、`Button` コントロールを追加します。

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. MainPage.xaml.h で、これらの事前宣言を `private` クラス宣言の `MainPage` セクションに追加します。

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. MainPage.xaml.cpp で、`Button_Click` イベント ハンドラーを実装します。

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. MainPage.xaml.cpp で、例に示すように `WriteFilesAsync` を実装します。

> [!TIP]

> `when_all` は、その結果、`task` を生成する、非ブロッキング関数です。 異なり[task::wait](reference/task-class.md#wait)ASTA (アプリケーション STA) スレッドでの UWP アプリでこの関数を呼び出しても安全になります。

###  <a name="when-any"></a> When_any 関数

`when_any` 関数は、一連のタスクの最初のタスクの完了後に完了するタスクを生成します。 この関数を返します、 [std::pair](../../standard-library/pair-structure.md)完了したタスクの結果とそのタスク セット内のインデックスを含むオブジェクト。

`when_any` 関数は、特に次のシナリオに役立ちます。

- 重複した操作。 多くの方法で実行できるアルゴリズムまたは操作を検討してください。 `when_any` 関数を使用すると、最初の操作を完了して残りの操作を取り消すように、操作を選択できます。

- インタリーブされた操作。 複数の操作を開始して、それらの操作のすべてが完了し、各操作が完了したら `when_any` 関数を使って結果を処理するようにできます。 1 つの操作が完了したら、1 つ以上の追加タスクを開始できます。

- 制限された操作。 `when_any` 関数を使用して、前のシナリオを拡張し、同時操作の数を制限することができます。

- 有効期限切れの操作。 `when_any` 関数を使用して、1 つ以上のタスクと特定の時間以降に完了する 1 つのタスクから選択することができます。

`when_all` と同様に、通常は継続を `when_any` と共に使用して、一連タスクの最初のタスクが終了した後に操作を実行します。 次の基本的な例では、`when_any` を使用して、他の 3 つのタスクの最初のタスクが完了したときに完了するタスクを作成します。

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

この例では、タスク ベースの継続を作成するために `task<pair<int, size_t>>` を指定することもできます。

> [!NOTE]
>  `when_all` と同様に、`when_any` に渡すタスクはすべて同じ型を返す必要があります。

次に示す例のように、`||` 構文を使用して、一連のタスクの最初のタスクの完了後に完了するタスクを生成することもできます。

`auto t = t1 || t2; // same as when_any`

> [!TIP]
>  同様`when_all`、`when_any`は非ブロッキングであり、ASTA スレッドでの UWP アプリで呼び出しても安全です。

##  <a name="delayed-tasks"></a> 遅延したタスクの実行

条件が満たされるまで、または外部イベントに応答してタスクを開始するまで、タスクの実行を遅延する必要がある場合があります。 たとえば、非同期プログラミングでは、I/O 完了のイベントに応答してタスクを開始する必要があります。

これを実現する 2 とおりの方法は、継続を使用するか、タスクを開始してタスクの処理関数の中でイベントを待つことです。 しかし、これらの方法の 1 つを使用できない場合もあります。 たとえば、継続を作成するためには、継続元タスクが必要です。 ただし、継続元タスクがないことができますを作成する、*タスクの完了イベント*し、後で使用可能になったときにその継続元タスクの完了イベントを連結します。 また、待機中のタスクはスレッドをブロックするため、タスクの完了イベントを使用して、非同期操作が完了したときに処理を行い、スレッドを解放することもできます。

[Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)クラスは、タスクのような構成を簡略化します。 `task` クラスと同様に、型パラメーター `T` は、タスクで生成される結果の型です。 タスクが値を返さない場合には、この型は `void` となります。 `T` は `const` 修飾子を使用できません。 通常、`task_completion_event` オブジェクトは、値が使用できるようになると通知する、スレッドまたはタスクに提供されます。 同時に、1 つ以上のタスクは、そのイベントのリスナーとして設定されます。 イベントが設定されると、リスナー タスクが完了し、継続が実行されるようにスケジュールされます。

使用する例については`task_completion_event`遅延後に完了するタスクを実装するを参照してください。[方法: タスクを作成するには、その完了後に、遅延](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)します。

##  <a name="task-groups"></a> タスク グループ

A*タスク グループ*タスクのコレクションを整理します。 タスク グループでは、ワーク スティーリング キューにタスクを置きます。 スケジューラはこのキューからタスクを削除し、使用できるコンピューティング リソースでそのタスクを実行します。 タスク グループにタスクを追加した場合、すべてのタスクが終了するまで待機することも、まだ開始されていないタスクを取り消すこともできます。

PPL を使用して、 [concurrency::task_group](reference/task-group-class.md)と[concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)タスクのグループを表すクラスと[concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md)クラスこれらのグループで実行されるタスクを表す。 `task_handle` クラスは、処理を行うコードをカプセル化します。 `task` クラスと同様に、この処理関数には、ラムダ関数、関数ポインター、または関数オブジェクトを使用できます。 通常、`task_handle` オブジェクトを直接操作する必要はありません。 代わりに、タスク グループに処理関数を渡します。タスク グループによって `task_handle` オブジェクトが作成および管理されます。

PPL タスク グループをこれら 2 つのカテゴリに分割する:*非構造化タスク グループ*と*タスク グループを構造化*します。 PPL では、`task_group` クラスを使用して非構造化タスク グループを表し、`structured_task_group` クラスを使用して構造化タスク グループを表します。

> [!IMPORTANT]

>  また、PPL を定義します、 [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)使用するアルゴリズムを`structured_task_group`一連のタスクを並列に実行するクラス。 `parallel_invoke` アルゴリズムにはより簡潔な構文が用意されているため、可能であれば `structured_task_group` クラスの代わりに使用することをお勧めします。 トピック[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)説明`parallel_invoke`さらに詳しく説明します。

`parallel_invoke` は、同時に実行する独立したタスクが複数あり、すべてのタスクが終了するまで待機してから処理を続行する必要がある場合に使用します。 この手法として呼ば*フォークと結合*並列処理します。 `task_group` は、同時に実行する独立したタスクが複数あり、それらのタスクが終了するタイミングがまだ先である場合に使用します。 たとえば、`task_group` オブジェクトにタスクを追加して、それらのタスクが別の関数や別のストレッドで終了するまで待機できます。

タスク グループでは、キャンセル処理の概念がサポートされています。 キャンセル処理を使用すると、操作全体を取り消すことをアクティブなすべてのタスクに通知できます。 また、キャンセル処理により、まだ開始されていないタスクが実行されるのを防止できます。 キャンセルの詳細については、次を参照してください。 [PPL における取り消し処理](cancellation-in-the-ppl.md)します。

また、ランタイムでは、例外処理モデルを使用することによって、タスクから例外をスローし、関連するタスク グループが終了するまで待機しているときにその例外を処理できます。 この例外処理モデルの詳細については、次を参照してください。[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)します。

##  <a name="comparing-groups"></a> Task_group structured_task_group の違いを比較します。

`task_group` クラスの代わりに `parallel_invoke` または `structured_task_group` を使用することが推奨されますが、可変個のタスクを実行する並列アルゴリズムやキャンセル処理のサポートが必要な並列アルゴリズムを記述する場合など、`structured_task_group` を使用した方がよい場合もあります。 ここでは、`task_group` クラスと `structured_task_group` クラスの違いについて説明します。

`task_group` クラスはスレッド セーフです。 したがって、複数のスレッドから `task_group` オブジェクトにタスクを追加したり、複数のスレッドから `task_group` オブジェクトに対して待機や取り消しの操作を行ったりしてもかまいません。 `structured_task_group` オブジェクトの構築と破棄は、同じ構文のスコープで行う必要があります。 また、`structured_task_group` オブジェクトに対する操作はすべて同じスレッドで行う必要があります。 このルールの例外は、 [::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)と[:is_canceling](reference/structured-task-group-class.md#is_canceling)メソッド。 子タスクでこれらのメソッドを呼び出すことで、任意のタイミングで親タスク グループを取り消したり、取り消し処理をチェックしたりできます。

その他のタスクを行うことができます、`task_group`オブジェクトを呼び出した後、 [::task_group::wait](reference/task-group-class.md#wait)または[concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait)メソッド。 逆で追加のタスクを実行する場合、`structured_task_group`オブジェクトを呼び出した後、 [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)または[::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait)メソッド、動作は未定義です。

`structured_task_group` クラスはスレッド間で同期されないため、実行に伴うオーバーヘッドが `task_group` クラスよりも少なくなります。 したがって、複数のスレッドから処理をスケジュールする必要のない問題に対処する場合に、`parallel_invoke` アルゴリズムを使用できないときは、`structured_task_group` クラスを使用すると、よりパフォーマンスの高いコードを作成できます。

`structured_task_group` オブジェクトを別の `structured_task_group` オブジェクト内で使用する場合は、外部オブジェクトが終了する前に内部オブジェクトが終了して破棄される必要があります。 `task_group` クラスの場合、外部グループが終了する前に、入れ子になったタスク グループが終了する必要はありません。

非構造化タスク グループと構造化タスク グループでは、さまざまな方法でタスク ハンドルを操作します。 `task_group` オブジェクトには処理関数を直接渡すことができます。`task_group` オブジェクトによってタスク ハンドルが自動的に作成および管理されます。 `structured_task_group` クラスを使用する場合は、タスクごとに `task_handle` オブジェクトを管理する必要があります。 各 `task_handle` オブジェクトは、関連する `structured_task_group` オブジェクトの有効期間を通じて有効である必要があります。 使用して、 [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task)関数を作成する、`task_handle`基本的な例を次に示すように、オブジェクトします。

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

可変個のタスクがある場合のタスク ハンドルを管理するには、スタック割り当てルーチンをなど使用[_malloca](../../c-runtime-library/reference/malloca.md)または std などのコンテナー クラス::[ベクター](../../standard-library/vector-class.md)します。

`task_group` と `structured_task_group` の両方でキャンセル処理がサポートされています。 キャンセルの詳細については、次を参照してください。 [PPL における取り消し処理](cancellation-in-the-ppl.md)します。

##  <a name="example"></a> 「例」

次の簡単な例では、タスク グループの操作方法を示します。 この例では、`parallel_invoke` アルゴリズムを使用して、2 つのタスクを同時に実行します。 各タスクでは、サブタスクを `task_group` オブジェクトに追加します。 `task_group` クラスを使用した場合、複数のタスクでタスクを同時に追加できることに注意してください。

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

この例のサンプル出力を次に示します。

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

`parallel_invoke` アルゴリズムではタスクを同時に実行するため、出力メッセージの順序が変わる可能性があります。

使用する方法を示す完全な例については、`parallel_invoke`アルゴリズムを参照してください[方法: parallel.invoke を使用して並列並べ替えルーチンを記述する](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)と[方法: parallel.invoke to Execute Parallel Operationsを使用して](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). 使用する完全な例については、`task_group`を参照してください、非同期フューチャを実装するクラス[チュートリアル: フューチャの実装](../../parallel/concrt/walkthrough-implementing-futures.md)します。

##  <a name="robust"></a> 信頼性の高いプログラミング

タスク、タスク グループ、および並列アルゴリズムを使用する場合は、キャンセル処理と例外処理の役割を十分に理解しておいてください。 たとえば、並列処理ツリーでタスクを取り消すと、子タスクも実行されなくなります。 そのため、アプリケーションで重要となる操作 (リソースの解放など) が子タスクのいずれかで実行されるような場合に問題となります。 また、子タスクが例外をスローすると、その例外がオブジェクトのデストラクターを介して反映され、アプリケーションで未定義の動作が発生する可能性があります。 これらのポイントを示す例を参照してください、[理解する方法のキャンセル機能と例外は、オブジェクトの破棄を影響を与える処理](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)並列パターン ライブラリに関するベスト プラクティス」セクション。 キャンセルと PPL での例外処理モデルの詳細については、次を参照してください。[キャンセル](../../parallel/concrt/cancellation-in-the-ppl.md)と[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)します。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[方法: 並列呼び出しを使用して並列並べ替えルーチンを記述する](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|`parallel_invoke` アルゴリズムを使用して、バイトニック ソート アルゴリズムのパフォーマンスを向上させる方法について説明します。|
|[方法: Parallel.Invoke を使用して並列操作を実行する](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|`parallel_invoke` アルゴリズムを使用して、共有データ ソースに対して複数の操作を実行するプログラムのパフォーマンスを向上させる方法について説明します。|
|[方法: 遅延後に完了するタスクを作成する](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|使用する方法を示しています、 `task`、 `cancellation_token_source`、 `cancellation_token`、および`task_completion_event`遅延後に完了するタスクを作成するためのクラス。|
|[チュートリアル: フューチャの実装](../../parallel/concrt/walkthrough-implementing-futures.md)|同時実行ランタイムの既存の機能を組み合わせて、より効果的に使用する方法を示します。|
|[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|同時実行アプリケーションの開発に不可欠なプログラミング モデルを提供する PPL について説明します。|

## <a name="reference"></a>参照

[task クラス (コンカレンシー ランタイム)](../../parallel/concrt/reference/task-class.md)

[task_completion_event クラス](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all 関数](reference/concurrency-namespace-functions.md#when_all)

[when_any 関数](reference/concurrency-namespace-functions.md#when_any)

[task_group クラス](reference/task-group-class.md)

[parallel_invoke 関数](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group クラス](../../parallel/concrt/reference/structured-task-group-class.md)
