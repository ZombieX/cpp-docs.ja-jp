---
title: CLR をターゲットにした C++ プログラムのコンパイル | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a375f93eaa164657964be7ad1ea2554ebc1986b8
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235400"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>チュートリアル: Visual Studio で CLR をターゲットにした C++ プログラムのコンパイル

.NET クラスを使用する Visual C++ プログラムを作成し、Visual Studio 開発環境を使用してそれをコンパイルすることができます。  
  
この手順では、独自の Visual C++ プログラムを入力するか、いずれかのサンプル プログラムを使用できます。 この手順で使用するサンプル プログラムでは、textfile.txt という名前のテキスト ファイルを作成し、プロジェクト ディレクトリに保存します。  
  
## <a name="prerequisites"></a>必須コンポーネント  

これらのトピックは、C++ 言語の基本を理解していることを前提としています。  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Visual Studio で新しいプロジェクトを作成して新しいソース ファイルを追加するには  
  
1. 新しいプロジェクトを作成します。 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
1. Visual C++ プロジェクトの種類から、**[CLR]**、**[CLR 空プロジェクト]** の順にクリックします。  

   > [!NOTE]
   > プロジェクトの種類として **[CLR 空プロジェクト]** (Visual Studio 2017 のみ) がない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左ウィンドウで、**[Visual Studio インストーラーを開く]** を選択します。 **[省略可能]** コンポーネント セクションの **[C++ によるデスクトップ開発]** で、"**C++/CLI サポート**" という名前のオプションをインストールします。<br/>
  
1. プロジェクト名を入力します。  
  
    既定では、プロジェクトを含むソリューションは新しいプロジェクトと同じ名前になりますが、別の名前を入力してもかまいません。 必要に応じて、プロジェクトの場所として別の場所を入力することもできます。  
  
    **[OK]** をクリックして、新しいプロジェクトを作成します。  
  
1. **ソリューション エクスプローラー**が表示されていない場合は、**[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。  
  
1. プロジェクトに新しいソース ファイルを追加します。  
  
    - **ソリューション エクスプローラー**で、**[ソース ファイル]** フォルダーを右クリックし、**[追加]** をポイントして、**[新しい項目]** をクリックします。  
  
    - **[C++ ファイル (.cpp)]** をクリックしてファイル名を入力し、**[追加]** をクリックします。  
  
    **ソリューション エクスプローラー**の**ソース ファイル** フォルダーに **.cpp** ファイルが表示されます。また、タブ付きウィンドウが表示され、ここでそのファイル内に含めるコードを入力します。  
  
1. Visual Studio で新しく作成されたタブをクリックして、有効な Visual C++ プログラムを入力するか、サンプル プログラムのいずれかをコピーして貼り付けます。  
  
    たとえば、(プログラミング ガイドの**ファイル処理と I/O** ノード内の) 「[方法: テキスト ファイルを記述する (C++/CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)」サンプル プログラムを使用できます。  
  
    サンプル プログラムを使用する場合は、.NET オブジェクトを作成するときに、`new` の代わりに `gcnew`キーワードを使用することと、`gcnew` がポインター (`*`) ではなくハンドル (`^`) を返すことに注意してください。  
  
    `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
    新しい Visual C++ 構文の詳細については、「[ランタイム プラットフォームのコンポーネントの拡張機能](../windows/component-extensions-for-runtime-platforms.md)」を参照してください。  
  
1. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
    **[出力]** ウィンドウに、ビルド ログの場所やビルドの状態を示すメッセージなど、コンパイルの進行状況に関する情報が表示されます。  
  
    ビルドを行わずに、プログラムを変更して実行する場合、ダイアログ ボックスにプロジェクトが有効期限切れであることが示される場合があります。 Visual Studio がアプリケーションをビルドするたびに入力を求めるのではなく、常にファイルの現在のバージョンを使用するようにする場合は、このダイアログでチェック ボックスを選択してから **[OK]** をクリックします。  
  
1. **[デバッグ]** メニューの **[デバッグなしで開始]** をクリックします。  
  
1. サンプル プログラムを使用した場合は、プログラムを実行するときに、テキスト ファイルが作成されたことを示すコマンド ウィンドウが表示されます。  
  
    これで **textfile.txt** テキスト ファイルがプロジェクトに配置されました。 このファイルはメモ帳を使用して開くことができます。  
  
    > [!NOTE]
    > 空の CLR プロジェクト テンプレートを選択すると、`/clr` コンパイラ オプションが自動的に設定されます。 これを確認するには、**ソリューション エクスプローラー**でプロジェクトを右クリックして、**[プロパティ]** をクリックしてから、**[構成プロパティ]** の **[全般]** ノードで **[共通言語ランタイム サポート]** オプションを確認します。  
  
## <a name="whats-next"></a>次の内容 

**前へ:** [チュートリアル: コマンド ラインでのネイティブ C++ プログラムのコンパイル](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
**次へ:** [チュートリアル: コマンド ラインでの C プログラムのコンパイル](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
  
## <a name="see-also"></a>参照  

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C/C++ プログラムのビルド](../build/building-c-cpp-programs.md)<br/>
