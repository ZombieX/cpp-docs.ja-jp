---
title: 致命的なエラー C1055 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6960d8168bd818e4d1baa30e5e54940e6e4dc2e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115451"
---
# <a name="fatal-error-c1055"></a>致命的なエラー C1055

コンパイラの制限: キーが足りません

ソース ファイルには、シンボルが多すぎますが含まれています。 コンパイラは、シンボル テーブルのハッシュ キー不足になりました。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. ソース ファイルをより小さなファイルに分割します。

1. 不要なヘッダー ファイルを削除します。

1. 新規に作成するのではなく、一時的およびグローバル変数を再利用します。