---
title: -GL (プログラム全体の最適化) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97561a63a21550cc06f29a95f6ddf05687758b83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723659"
---
# <a name="gl-whole-program-optimization"></a>/GL (プログラム全体の最適化)

プログラム全体の最適化を有効にします。

## <a name="syntax"></a>構文

```
/GL[-]
```

## <a name="remarks"></a>Remarks

プログラム全体の最適化は、コンパイラが、プログラムのすべてのモジュールの情報を使用した最適化を実行できます。 プログラム全体の最適化されていない場合の最適化の実行、ごとのモジュール (コンパイル単位)。

プログラム全体の最適化は既定で無効と明示的に有効にする必要があります。 ただし、それを明示的に無効にすることがも **/GL-** します。

すべてのモジュールについては、コンパイラでは次のことができます。

- 関数の境界を越えて、レジスタの使用を最適化します。

- グローバル データの読み込みおよび格納の数を減らします変更の追跡の方の操作を行います。

- 読み込みおよび格納の数を減らす、一連の可能なポインターによって変更された項目を逆参照追跡の方の操作を行います。

- インライン関数が別のモジュールで定義されている場合でも、モジュール内の関数。

生成された .obj ファイル **/GL**はこのようなリンカー ユーティリティを使用できません[EDITBIN](../../build/reference/editbin-reference.md)と[DUMPBIN](../../build/reference/dumpbin-reference.md)します。

プログラムをコンパイルする場合 **/GL**と[/c](../../build/reference/c-compile-without-linking.md)、/LTCG リンカー オプションを使用して、出力ファイルを作成する必要があります。

[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)では使用できません **/GL**

生成されたファイルの形式の **/GL**現在のバージョンでできない可能性がありますそれ以降のバージョンの Visual C で読み取ることです。 生成された .obj ファイルから成る .lib ファイルを出荷する必要があります **/GL**ユーザーを現在および将来の使用が予想されるすべてのバージョンの Visual C の .lib ファイルのコピーを同梱する意思がないです。

生成された .obj ファイル **/GL**プリコンパイル済みヘッダー ファイルは .lib ファイルを生成したのと同じコンピューターにリンクする場合を除き、.lib ファイルの作成に使用する必要があります、 **/GL** .obj ファイル。 .Obj ファイルのプリコンパイル済みヘッダー ファイルからの情報は、リンク時に必要になります。

使用可能な最適化と、プログラム全体の最適化の制限事項の詳細については、次を参照してください。 [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)します。  **/GL**もでは使用できるガイド付き最適化のプロファイルは、/LTCG を参照してください。  ガイド付き最適化と関数の最適化のプロファイル ガイド付きの順序付けをするかどうかのプロファイルのコンパイルをするときに使用してコンパイルする必要があります[/Gy](../../build/reference/gy-enable-function-level-linking.md)またはコンパイラ オプション/Gy ことを意味します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. 参照してください[/LTCG (リンク時コード生成)](../../build/reference/ltcg-link-time-code-generation.md)を指定する方法については **/GL**開発環境。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)