---
title: リンカーを呼び出す CL |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed6c968b86192ae79c0c921f8b3fababc596c9a2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713831"
---
# <a name="cl-invokes-the-linker"></a>リンカーを呼び出す CL

/C オプションを使用しない限り、コンパイル後に自動的にリンカーを呼び出す CL します。 CL は、コンパイル時に作成された .obj ファイルの名前とその他のコマンドラインで指定されたファイルの名前をリンカーに渡します。 リンカーは、環境変数 LINK に示すオプションを使用します。 /Link オプションを使用して、CL のコマンド ラインでリンカー オプションを指定することができます。 /Link オプションに続くオプションのリンクの環境変数でオーバーライドします。 次の表に、オプションでは、リンクを抑制します。

|オプション|説明|
|------------|-----------------|
|/c|リンクなしでコンパイルします。|
|/E、/EP/P|コンパイルとリンクを使用せずに前処理します。|
|/Zg|関数プロトタイプを生成します。|
|/Zs|構文を確認します。|

リンクの詳細については、次を参照してください。[リンカー オプション](../../build/reference/linker-options.md)します。

## <a name="example"></a>例

次の 3 つの C ソース ファイルをコンパイルすることを前提としています: MAIN.c、MOD1.c、および MOD2.c します。 各ファイルには、別のファイルで定義されている関数の呼び出しが含まれます。

- 関数を呼び出す MAIN.c `func1` MOD1.c と関数で`func2`MOD2.c で。

- 標準ライブラリ関数を呼び出す MOD1.c`printf_s`と`scanf_s`します。

- MOD2.c という名前のグラフィックス関数を呼び出す`myline`と`mycircle`、MYGRAPH.lib という名前のライブラリで定義されています。

このプログラムをビルドするには、次のコマンドラインでコンパイルします。

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

まず、CL は C ソース ファイルをコンパイルし、MAIN.obj、MOD1.obj、および MOD2.obj オブジェクト ファイルを作成します。コンパイラは、標準ライブラリの名前を各 .obj ファイルに配置します。 詳細については、次を参照してください。[ランタイム ライブラリの使用](../../build/reference/md-mt-ld-use-run-time-library.md)します。

CL は、名前、MYGRAPH.lib と共に、.obj ファイルの名前をリンカーに渡します。 リンカーは、次のように外部参照を解決します。

1. MAIN.obj への参照で`func1`MOD1.obj; の定義を使用して解決への参照を`func2`MOD2.obj の定義を使用して解決されます。

1. MOD1.obj への参照で`printf_s`と`scanf_s`MOD1.obj 内という名前のリンカーが検索するライブラリで定義を使用して解決されます。

1. MOD2.obj への参照で`myline`と`mycircle`MYGRAPH.lib の定義を使用して解決されます。

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)