---
title: コンパイラの警告 (レベル 1) C4445 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4445
dev_langs:
- C++
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80b3e13f0f7271a38d71c65efa65f104e44aa475
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079948"
---
# <a name="compiler-warning-level-1-c4445"></a>コンパイラの警告 (レベル 1) C4445

'function': WinRT またはマネージド型で、仮想関数をプライベートにすることはできません

仮想関数がプライベートである場合、派生型からアクセスできなくなります。 このエラーを解決するには、仮想メンバー関数のアクセシビリティをプロテクトまたはパブリックに変更します。