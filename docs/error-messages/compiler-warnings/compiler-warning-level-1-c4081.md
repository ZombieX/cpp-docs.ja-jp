---
title: コンパイラの警告 (レベル 1) C4081 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4081
dev_langs:
- C++
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48834d2ba379ae9a5fd3c2d4ba976f29b1a8c717
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034344"
---
# <a name="compiler-warning-level-1-c4081"></a>コンパイラの警告 (レベル 1) C4081

'token1' が必要でしたが、'token2' が見つかりました

コンパイラでは、このコンテキストで別のトークンが必要でした。

## <a name="example"></a>例

```
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```