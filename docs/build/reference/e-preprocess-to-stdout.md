---
title: -E (stdout に前処理する) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /e
dev_langs:
- C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48517f4469f203f5e29fbaa4ec105a3e36aafb44
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720272"
---
# <a name="e-preprocess-to-stdout"></a>/E (プリプロセス出力の標準出力へのコピー)

C および C++ ソース ファイルを前処理し、前処理済みファイルを標準出力デバイスにコピーします。

## <a name="syntax"></a>構文

```
/E
```

## <a name="remarks"></a>Remarks

このプロセスですべてのプリプロセッサ ディレクティブを実施する、マクロの展開を実行すると、およびコメントを削除します。 前処理済みの出力内のコメントを保持するために使用して、 [(保持プリプロセス時のコメント)/C](../../build/reference/c-preserve-comments-during-preprocessing.md)コンパイラ オプションもします。

**/E**追加`#line`ディレクティブを先頭と末尾各インクルード ファイルの条件付きコンパイルのプリプロセッサ ディレクティブによって削除された行に出力します。 これらのディレクティブは、前処理済みファイルの行を再設定します。 その結果、処理の後のステージ中に生成されたエラーは、前処理済みファイル内の行ではなく、元のソース ファイルの行番号を参照してください。

**/E**オプションはコンパイルを中止します。 Compilation の前処理済みファイルを再送信する必要があります。 **/E**から出力ファイルも生成されません、 **/FA**、 **/Fa**、および **/Fm**オプション。 詳細については、次を参照してください。 [/FA、/Fa (リスティング ファイル)](../../build/reference/fa-fa-listing-file.md)と[/Fm (マップ ファイルの名前)](../../build/reference/fm-name-mapfile.md)します。

抑制する`#line`ディレクティブを使用して、 [/EP (#line ディレクティブなしの stdout に前処理する)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)オプションを使用します。

前処理済みの出力ではなくファイルを送信する`stdout`を使用して、 [/P (ファイルへのプリプロセス)](../../build/reference/p-preprocess-to-a-file.md)オプションを使用します。

抑制する`#line`ディレクティブと送信ファイル、前処理済みの出力を使用して、 **/P**と **/EP**化します。

プリコンパイル済みヘッダーを使用することはできません、 **/E**オプション。

別のファイルの前処理、スペースはトークンの後しない出力されることに注意してください。 これは、不正なプログラムでまたはが意図しない副作用です。 次のプログラムが正常にコンパイルされます。

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

ただし、使用してコンパイルする場合。

```
cl -E test.cpp > test2.cpp
```

`int main` test2.cpp で正しくされません`intmain`します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. コンパイラ オプションを入力、**追加オプション**ボックス。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>

## <a name="example"></a>例

次のコマンドラインの前処理`ADD.C`、コメントを保持、追加`#line`ディレクティブでは、標準出力デバイス上の結果を表示します。

```
CL /E /C ADD.C
```

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)