---
title: -MD、-MT、-LD (ランタイム ライブラリの使用) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
dev_langs:
- C++
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aefd61d724f7716392b5fd2d15ef3a2f9ff0006
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890232"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD、/MT、/LD (ランタイム ライブラリの使用)

マルチスレッド モジュールが DLL であるかどうかを指定し、ランタイム ライブラリのリテール バージョンまたはデバッグ バージョンを指定します。

## <a name="syntax"></a>構文

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Remarks

|オプション|説明|
|------------|-----------------|
|**/MD**|アプリケーションでランタイム ライブラリのマルチスレッド対応および DLL 対応バージョンが使用されます。 `_MT` および `_DLL` を定義し、コンパイラにライブラリ名 MSVCRT.lib を .obj ファイルに挿入させます。<br /><br /> このオプションを使用してコンパイルされたアプリケーションは、MSVCRT.lib に静的にリンクされます。 このライブラリには、リンカーが外部参照を解決できるようにするコード レイヤーが用意されています。 実際に動くコードは MSVCR に含まれている*versionnumber*します。DLL は、MSVCRT.lib にリンクされているアプリケーションを実行時に使用できる必要があります。|
|**/MDd**|`_DEBUG`、`_MT`、および `_DLL` を定義します。アプリケーションで、マルチスレッド対応バージョンおよび DLL 対応バージョンのランタイム ライブラリが使用されます。 また、コンパイラによって、ライブラリ名 MSVCRTD.lib が .obj ファイルに挿入されます。|
|**/MT**|アプリケーションで、マルチスレッド バージョンの静的なランタイム ライブラリが使用されます。 `_MT` を定義します。また、コンパイラにライブラリ名 LIBCMT.lib を .obj ファイルに挿入させるため、リンカーは LIBCMT.lib を使って外部シンボルを解決します。|
|**/MTd**|`_DEBUG` および `_MT` を定義します。 このオプションによって、リンカーが LIBCMTD.lib を使用して外部シンボルを解決できるように、コンパイラによりライブラリ名 LIBCMTD.lib が .obj ファイルに挿入されます。|
|**/LD**|DLL を作成します。<br /><br /> パス、 **/DLL**リンカーにオプション。 リンカーは `DllMain` 関数の有無を確認します。 `DllMain` 関数が記述されていないと、TRUE を返す `DllMain` 関数がリンク時に自動的に挿入されます。<br /><br /> DLL の起動コードをリンクします。<br /><br /> コマンド ラインでエクスポート (.exp) ファイルが指定されていない場合は、インポート ライブラリ (.lib) を作成します。 このインポート ライブラリを、DLL を呼び出すアプリケーションにリンクしてください。<br /><br /> 解釈[/Fe (EXE ファイルの名前)](../../build/reference/fe-name-exe-file.md) .exe ファイルではなく、DLL の名前を付けるとします。 既定では、プログラム名になります*basename*の代わりに .dll *basename*.exe です。<br /><br /> 意味 **/MT**明示的に指定しない限り **/MD**します。|
|**/LDd**|デバッグ DLL を作成します。 `_MT` および `_DEBUG` を定義します。|

C ランタイム ライブラリと指定してコンパイルしたときに使用されるライブラリの詳細については[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)を参照してください[CRT ライブラリの機能](../../c-runtime-library/crt-library-features.md)します。

リンカーの特定の呼び出しに渡されるすべてのモジュールを同じランタイム ライブラリ コンパイラ オプションでコンパイルする必要があります (**/MD**、 **/MT**、 **/LD**)。

ランタイム ライブラリのデバッグ バージョンを使用する方法の詳細については、次を参照してください。 [C ランタイム ライブラリ リファレンス](../../c-runtime-library/c-run-time-library-reference.md)します。

詳細については、Dll は、次を参照してください。 [Visual c の Dll](../../build/dlls-in-visual-cpp.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 展開、 **C/C++** フォルダー。

1. 選択、**コード生成**プロパティ ページ。

1. 変更、**ランタイム ライブラリ**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)