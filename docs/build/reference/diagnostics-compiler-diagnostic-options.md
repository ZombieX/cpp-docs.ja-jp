---
title: -診断 (コンパイラの診断オプション) |Microsoft Docs
ms.custom: ''
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs:
- C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d0e6567f8666df4ec170ad7911ef08f5a1d335
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861630"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/diagnostics (コンパイラの診断オプション)

使用して、 **/diagnostics**コンパイラ オプションをエラーと警告場所の情報の表示形式を指定します。

## <a name="syntax"></a>構文

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Remarks

Visual Studio 2017 以降、このオプションはサポートされています。

**/Diagnostics**コンパイラ オプションは、エラーおよび警告情報の表示を制御します。

**/Diagnostics:classic**オプションの既定値は、問題が見つかった行番号のみを報告します。

**/Diagnostics:column**オプションにも、問題が検出された場所の列が含まれています。 特定の言語コンストラクトまたは問題の原因となっている文字を特定できます。

**/Diagnostics:caret**オプションには、問題が見つかり、キャレット (^) を行のコードで問題が検出された場所の下に配置場所の列が含まれています。

場合によっては、コンパイラが発生した問題を検出しないください。 たとえば、不足しているセミコロンに検出できない可能性まで、他の予期しないシンボルが発生しました。 列が報告され、キャレットは、コンパイラは検出する何らかの問題がエラーが発生していないことが、修正を行う必要がありますに配置されます。

**/Diagnostics**オプションは、Visual Studio 2017 以降を使用します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの開く**プロパティ ページ** ダイアログ ボックス。

1. **構成プロパティ**、展開、 **C/C++** フォルダーを選択し、**全般**プロパティ ページ。

1. ドロップダウン コントロールを使用して、**診断形式**フィールド、診断を選択するオプションが表示されます。 選択**OK**または**適用**変更を保存します。

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)
