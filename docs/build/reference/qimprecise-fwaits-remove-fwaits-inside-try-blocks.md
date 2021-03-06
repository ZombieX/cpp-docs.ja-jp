---
title: -Qimprecise_fwaits (Try ブロック内部の fwaits を削除) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cad23ebdd2289791b50b0e956368b934fe0f1087
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385197"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (try ブロック内部の fwaits を削除する)

削除、`fwait`コマンドの内部`try`ブロックを使用する場合、 [/fp: を除く](../../build/reference/fp-specify-floating-point-behavior.md)コンパイラ オプション。

## <a name="syntax"></a>構文

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Remarks

このオプションには効果がない場合は **/fp: 除く**も指定されていません。 指定した場合、 **/fp: を除く**オプション、コンパイラが挿入されます、`fwait`コマンド内のコードの各行の周りを`try`ブロック。 これにより、コンパイラは、特定の例外が発生したコード行を識別できます。 **/Qimprecise_fwaits**内部削除`fwait`手順については、周囲の待機のみを残して、`try`ブロックします。 これは、パフォーマンスは向上しますが、コンパイラは指定できる`try`ブロック、例外では、どの行が発生します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](../../build/reference/q-options-low-level-operations.md)<br/>
[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)