---
title: -Fe (EXE ファイルの名前) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fe
dev_langs:
- C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad2683f79fdca845245fd266555e688aa8cf7374
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716236"
---
# <a name="fe-name-exe-file"></a>/Fe (EXE ファイルの名前の指定)

名前とディレクトリの .exe ファイルまたはコンパイラによって作成された DLL を指定します。

## <a name="syntax"></a>構文

> **/Fe**[_pathname_] **/Fe:** _パス名_

### <a name="arguments"></a>引数

*pathname*<br/>
相対パスまたは絶対パスと、基本ファイル名またはディレクトリ、または生成された実行可能ファイルを使用する基本ファイル名への相対または絶対パス。

## <a name="remarks"></a>Remarks

**/Fe**オプションでは、出力ディレクトリ、出力実行可能ファイル名、またはその生成された実行可能ファイルの両方を指定できます。 場合*pathname*パスの区切り文字で終わる (**&#92;**)、出力ディレクトリのみを指定すると見なされます。 それ以外の場合の最後のコンポーネント*pathname*は出力ファイルの基本名、およびの残りの部分として使用*pathname*出力ディレクトリを指定します。 場合*pathname*パスの区切り記号はありません。 現在のディレクトリに出力ファイル名を指定すると見なされます。 *Pathname*二重引用符で囲む必要があります (**"**) スペースなどの短いパスにすることはできませんのすべての文字が含まれている場合拡張文字、またはパス コンポーネント 8 文字より長い。

ときに、 **/Fe**オプションが指定されていない、またはで名前が指定されていない場合、基本ファイル*pathname*コンパイラは、出力ファイルの指定された最初のソースまたはオブジェクトのファイル ベース名を使用して、既定の名前コマンドラインと拡張子が .exe または .dll します。

指定した場合、 [(コンパイル リンクなしの)/c](c-compile-without-linking.md)オプション、 **/Fe**も何も起こりません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 開く、**構成プロパティ** > **リンカー** > **全般**プロパティ ページ。

1. 変更、**出力ファイル**プロパティ。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>

## <a name="example"></a>例

次のコマンドラインは、コンパイルし、現在のディレクトリ内のすべての C ソース ファイルをリンクします。 結果として得られる実行可能ファイルでは、PROCESS.exe という名前し、"C:\Users\User Name\repos\My Project\bin"ディレクトリに作成されます。

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>例

次のコマンドラインでの実行可能ファイルを作成します`C:\BIN`で現在のディレクトリ内の最初のソース ファイルと同じ基本名。

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](../../build/reference/output-file-f-options.md)<br/>
[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)<br/>
[パス名の指定](../../build/reference/specifying-the-pathname.md)<br/>
