---
title: ワイルドカードの展開 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cac6b61176b1559ea5810dc061638642926b3969
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077075"
---
# <a name="wildcard-expansion"></a>ワイルドカードの展開

## <a name="microsoft-specific"></a>Microsoft 固有の仕様

コマンド ラインでファイル名とパスの引数を指定するときに、ワイルドカード (疑問符 (?) およびアスタリスク (*)) を使用できます。

コマンドライン引数はというルーチンによって処理される`_setargv`(または`_wsetargv`ワイド文字環境で)、ワイルドカードの展開で個別の文字列に既定ではありません、`argv`文字列配列。 ワイルドカードの展開の有効化の詳細についてを参照してください[ワイルドカード引数の展開](../c-language/expanding-wildcard-arguments.md)します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[main: プログラムの起動](../cpp/main-program-startup.md)