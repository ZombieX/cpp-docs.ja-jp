---
title: デリゲート (C + + CX) |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42ca9673efe45ca816208e87ef0f0153d069e4a9
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108428"
---
# <a name="delegates-ccx"></a>デリゲート (C++/CX)

`delegate`キーワードの使用を標準 C++ での関数オブジェクトの Windows ランタイムと等価な参照型を宣言します。 関数シグネチャに似たデリゲート宣言。これは、ラップされた関数が持つ必要のある、戻り値の型およびパラメーターの型を指定します。 これは、ユーザー定義のデリゲート宣言です。

```cpp
public delegate void PrimeFoundHandler(int result);
```

多くの場合、デリゲートはイベントと一緒に使用されます。 イベントは、デリゲート型を持ちます。これは、クラスがインターフェイスの型を持つことができるのとよく似た概念です。 デリゲートは、イベント ハンドラーが適切に満たすコントラクトを表します。 既に定義されているデリゲートに等しい型を持つイベント クラスのメンバーを次に示します。

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

クライアントに公開されるデリゲートを宣言する、Windows ランタイムのアプリケーション バイナリ インターフェイスを使用して[Windows::Foundation::TypedEventHandler\<TSender, TResult >](https://msdn.microsoft.com/library/windows/apps/br225997.aspx)します。 このデリゲートには、デリゲートが Javascript クライアントによって利用できるようにする、事前定義されたプロキシとスタブ バイナリがあります。

## <a name="consuming-delegates"></a>デリゲートの利用

ユニバーサル Windows プラットフォーム アプリを作成するときに頻繁に使用する Windows ランタイム クラスによって公開されるイベントの種類としてのデリゲート。 イベントにサブスクライブするには、デリゲートの署名に一致する関数 (ラムダ) を指定することで、そのデリゲート型のインスタンスを作成します。 そして、 `+=` 演算子を使用して、デリゲート オブジェクトをクラスのイベント メンバーに渡します。 これは、イベントのサブスクライブと呼ばれます。 クラスのインスタンスがイベントを "発生" させると、ユーザーのオブジェクトやその他のオブジェクトによって追加された他のハンドラーと共に、関数が呼び出されます。

> [!TIP]
> Visual Studio は、イベント ハンドラーを作成するときに便利です。 たとえば、イベント ハンドラーを XAML マークアップで指定すると、ツール ヒントが表示されます。 ツール ヒントが選択されると、Visual Studio は、自動的にイベント ハンドラー メソッドを作成し、パブリッシャー クラスのイベントに関連付けます。

次の例に、基本的なパターンを示します。 `Windows::Foundation::TypedEventHandler` はデリゲート型です。 ハンドラー関数は、名前付き関数を使用して生成されます。

app.h で:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

app.cpp で:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> 細心の注意を払って循環参照を回避する場合を除き、一般にイベント ハンドラーにはラムダではなく名前付き関数を使用する方が適しています。 名前付き関数では弱い参照によって "this" ポインターをキャプチャしますが、ラムダでは強い参照によって "this" ポインターをキャプチャし、循環参照を作成します。 詳細については、次を参照してください。[弱い参照および中断サイクル](../cppcx/weak-references-and-breaking-cycles-c-cx.md)します。

慣例により、Windows ランタイムによって定義されているイベント ハンドラー デリゲートの名前があるフォーム * EventHandler — などの RoutedEventHandler、SizeChangedEventHandler、suspendingeventhandler します。 同様に、慣例に基づき、イベント ハンドラー デリゲートは 2 つのパラメーターを持ち、void を返します。 型パラメーターがないデリゲートでは、最初のパラメーターは [Platform::Object^](../cppcx/platform-object-class.md)型です。これは、イベントを発生させたオブジェクトである送信元への参照を保持します。 イベント ハンドラー メソッドで引数を使用する前に、元の型にキャスト バックする必要があります。 型パラメーターを持つイベント ハンドラー デリゲートでは、最初の型パラメーターは送信元の種類を指定し、2 番目のパラメーターはイベントに関する情報を保持する ref クラスへのハンドルです。 慣例により、そのクラスの名前が\*EventArgs。 たとえば、RoutedEventHandler デリゲートには RoutedEventArgs^ 型の 2 番目のパラメーターがあり、DragEventHander には DragEventArgs^ 型の 2 番目のパラメーターがあります。

名前付け規則により、非同期操作が完了したときに実行されるコードをラップするデリゲートには、*CompletedHandler という名前が付けられます。 これらのデリゲートは、イベントではなくクラスのプロパティとして定義されます。 したがって、サブスクライブするために `+=` 演算子を使用する必要はありません。デリゲート オブジェクトをプロパティに割り当てるだけです。

> [!TIP]
> C++ IntelliSense ではデリゲート署名がフルに表示されないため、EventArgs パラメーターの特定の型を判断するための役には立ちません。 型を見つけるには、 **オブジェクト** ブラウザーでデリゲートの `Invoke` メソッドを確認します。

## <a name="creating-custom-delegates"></a>カスタム デリゲートの作成

イベント ハンドラーを定義する、またはコンシューマーを Windows ランタイム コンポーネントに渡すカスタム機能を有効にする、独自のデリゲートを定義できます。 他の Windows ランタイム型のようには、パブリック デリゲートをジェネリックとして宣言にすることはできません。

### <a name="declaration"></a>宣言

デリゲートの宣言は関数宣言に似ていますが、デリゲートは型である点が異なります。 クラス宣言の内部にデリゲート宣言を入れ子にすることもできますが、通常は名前空間スコープでデリゲートを宣言します。 次のデリゲートは、入力として `ContactInfo^` を受け取って `Platform::String^`を返す関数をカプセル化します。

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

デリゲート型を宣言した後、その型のクラス メンバー、またはパラメーターとしてその型のオブジェクトを受け取るメソッドを宣言できます。 メソッドまたは関数は、デリゲート型を返すこともできます。 次の例では、 `ToCustomString` メソッドは入力パラメーターとしてデリゲートを受け取ります。 このメソッドを使用すると、 `ContactInfo` オブジェクトのパブリック プロパティの一部またはすべてから文字列を構築するカスタム関数を、クライアント コードで提供することができます。

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> 使用する、"^"は任意の Windows ランタイムで型を参照するのと同じように、デリゲート型を参照するときをシンボルします。

イベント宣言には常にデリゲート型が含まれます。 この例は、一般的なデリゲートを示しています。 Windows ランタイムの型シグネチャ。

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

`Click` クラスの `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` イベントは、 `RoutedEventHandler`型です。 詳細については、「 [Events](../cppcx/events-c-cx.md)」を参照してください。

クライアント コードでは、 `ref new` を使用し、デリゲートのシグネチャと互換性のあるラムダを提供することで、まずデリゲート インスタンスを構築し、カスタム動作を定義します。

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

次に、メンバー関数を呼び出し、デリゲートを渡します。 `ci` が `ContactInfo^` インスタンスであり、 `textBlock` が XAML `TextBlock^`であると想定します。

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

次の例では、クライアント アプリは内の各項目に対してデリゲートを実行する Windows ランタイム コンポーネントのパブリック メソッドにカスタム デリゲートを渡します、 `Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>構築

次のいずれかのオブジェクトからデリゲートを構築できます。

- ラムダ

- 静的関数

- メンバーへのポインター

- std::function

次の例は、これらのオブジェクトからデリゲートを構築する方法を示しています。 構築に使用したオブジェクトの種類に関係なく、デリゲートの利用方法はまったく同じです。

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> "this" ポインターをキャプチャするラムダを使用する場合は、ラムダを終了する前に `-=` 演算子を使用し、明示的にイベントから登録解除してください。 詳細については、「[イベント](../cppcx/events-c-cx.md)」を参照してください。

### <a name="generic-delegates"></a>汎用デリゲート

C++/CX 内の汎用デリゲートには、ジェネリック クラスの宣言に似た制限があります。 これらを public として宣言することはできません。 プライベートまたは内部の汎用デリゲートを宣言し、C++ から利用することができますが、このデリゲートは .winmd のメタデータに対して出力されないため、.NET クライアントや JavaScript クライアントから利用することは実装できません。 この例では、次のように C++ でのみ利用できる汎用デリゲートを宣言します。

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

次の例では、クラス定義の内部で、デリゲートの特化されたインスタンスを宣言します。

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>デリゲートとスレッド

関数オブジェクトと同様に、デリゲートには将来いつか実行されるコードが含まれます。 デリゲートを作成して渡すコードと、デリゲートを受け取って実行する関数が同じスレッドで実行されている場合、動作は比較的簡単です。 そのスレッドが UI スレッドの場合、デリゲートは XAML コントロールなどのユーザー インターフェイス オブジェクトを直接処理できます。

クライアント アプリが、スレッド アパートメントで実行され、そのコンポーネントへのデリゲートを提供します。 Windows ランタイム コンポーネントを読み込む場合、既定では、デリゲートが呼び出される STA スレッドで直接。 ほとんどの Windows ランタイム コンポーネントは、STA または MTA で実行できます。

デリゲートを実行するコードが別のスレッド (concurrency::task オブジェクトのコンテキスト内など) で実行される場合は、共有データへのアクセスを同期する必要があります。 たとえば、デリゲートにベクターへの参照が含まれ、XAML コントロールが同じベクターへの参照を持つ場合は、デリゲートと XAML コントロールが同時にベクターにアクセスしようとしたときに発生する可能性のあるデッドロックや競合状態を回避する手順を実行する必要があります。 また、デリゲートが呼び出される前にスコープ外に出る可能性がある参照ローカル変数によってデリゲートがキャプチャを試みないように注意する必要もあります。

作成したデリゲートがそれを作成したスレッドと同じスレッドでコールバックされるようにする場合 (MTA アパートメントで実行されるコンポーネントにデリゲートを渡し、それが作成者と同じスレッドで呼び出されるようにする場合など) は、2 つ目の `CallbackContext` パラメーターを受け取るデリゲート コンストラクターのオーバーロードを使用します。 このオーバーロードは、登録されたプロキシ/スタブを持つデリゲートでのみ使用してください。Windows.winmd で定義されたすべてのデリゲートが登録されているわけではありません。

.NET でのイベント ハンドラーの扱いに慣れている場合は、イベントを発生させる前に、イベントのローカル コピーを作成することが推奨されている点を理解しているはずです。 この結果、イベントが呼び出される直前にイベント ハンドラーが削除される可能性がある、という競合状態を回避できます。 C++/CX では、イベント ハンドラーが追加または削除されたときに新しいハンドラーの一覧が作成されるため、この作業を実行する必要はありません。 C++ オブジェクトはイベントを発生させる前に、ハンドラーの一覧の参照カウントをインクリメントするため、すべてのハンドラーが有効であることが保証されます。 ただし、このことは同時に、利用側スレッドでイベント ハンドラーを削除した場合でも、発行側オブジェクトがそのリストのコピーを使用して引き続き動作している状況では (もうそのコピーは古いのですが)、依然としてそのハンドラーが呼び出される可能性があることを意味します。 発行側オブジェクトは、自らが次にそのイベントを発生させるまでは、更新されたリストを取得しません。

## <a name="see-also"></a>関連項目

[型システム](../cppcx/type-system-c-cx.md)<br/>
[Visual C 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)