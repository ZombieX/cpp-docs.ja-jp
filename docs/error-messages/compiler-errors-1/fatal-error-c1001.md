---
title: 致命的なエラー C1001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6363694dbd7f1a7ebfcd58cad030dfecf7f38397
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098200"
---
# <a name="fatal-error-c1001"></a>致命的なエラー C1001

> 内部コンパイラ ERROR(compiler file *file*, line *number*)

コンパイラは、解析中に特定の式と最適化オプション、または問題の組み合わせにより多くの場合、構成用の正しいコードを生成できません。 コンパイラ ファイルが一覧表示に utc または C2 パス セグメントがある場合は、おそらく最適化エラー。 ファイルが cxxfe または c1xx のパス セグメントまたは msc1.cpp が場合、は、おそらくパーサー エラーです。 Cl.exe の場合は、という名前のファイルはありませんその他の情報です。

多くの場合、1 つまたは複数の最適化オプションを削除することによって最適化の問題を修正できます。 どのオプションがあるエラーを確認するには、エラー メッセージは表示されなくなるまで時および再コンパイル オプションを 1 つを削除します。 オプションの責任に最もよく[/Og (グローバルの最適化)](../../build/reference/og-global-optimizations.md)と[/Oi (組み込み関数の生成)](../../build/reference/oi-generate-intrinsic-functions.md)します。 なる最適化オプションを決めたら、関数を使用してエラーが発生した無効ことができます、[最適化](../../preprocessor/optimize.md)プラグマ、続行、モジュールの残りのオプションを使用するとします。 最適化オプションの詳細については、次を参照してください。[最適化のベスト プラクティス](../../build/reference/optimization-best-practices.md)します。

最適化が、エラーの場合は、エラーが報告された行または数行のコードをその前後の書き直しをお試しください。 方法は、コンパイラは前処理した後は、コードを表示、使用することができます、 [/P (ファイルへのプリプロセス)](../../build/reference/p-preprocess-to-a-file.md)オプション。

エラーの原因を特定する方法と、内部コンパイラ エラーを Microsoft に報告する方法の詳細については、次を参照してください。 [Visual c ツールセットで問題を報告する方法](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)します。