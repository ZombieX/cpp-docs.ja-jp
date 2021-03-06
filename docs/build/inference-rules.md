---
title: 推論規則 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed45e5ad61ea1cc50172cd86716b357baa64fa39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724387"
---
# <a name="inference-rules"></a>推論規則

推論規則は、コマンド ターゲットを更新およびターゲットの依存関係を推論するを指定します。 推論規則の拡張機能が 1 つのターゲットと一致し、同じ基本名がある依存します。 推論規則には、ユーザー定義または定義済みです。定義済みの規則を再定義することができます。

コマンド、古いの依存関係がない場合、[します。サフィックス](../build/dot-directives.md)依存ファイルの拡張子と一致するターゲットと、既存のルールが現在または指定したディレクトリにファイル (nmake の) 使用されます。 1 つ以上のルールが、既存のファイルと一致する場合、**します。サフィックス**リストを使用して、決定; 一覧の優先順位は左から右にします。 依存ファイルが存在しないが別の記述ブロックのターゲットとして表示されない場合は、推論規則から作成できます不足している依存する別のファイルと同じベース名に置き換えます。 記述ブロックのターゲットには、依存ファイルやコマンドがなければ、推論規則は、ターゲットを更新できます。 推論規則は、記述ブロックが存在しない場合でも、コマンド ライン ターゲットをビルドできます。 (Nmake の) は、明示的な依存ファイルが指定した場合でも、推論による依存ファイルのルールを呼び出すことができます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[ルールを定義します。](../build/defining-a-rule.md)

[バッチモード規則](../build/batch-mode-rules.md)

[定義済みの規則](../build/predefined-rules.md)

[推論による依存ファイルと規則](../build/inferred-dependents-and-rules.md)

[推論規則の優先順位](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>関連項目

[NMAKE リファレンス](../build/nmake-reference.md)