---
title: コンパイラ エラー C2611 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2611
dev_langs:
- C++
helpviewer_keywords:
- C2611
ms.assetid: 3f2d5253-f24f-4724-83d0-6b2aa6a4e551
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 728d22a7af72232618716e665b241188773cd66c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031289"
---
# <a name="compiler-error-c2611"></a>コンパイラ エラー C2611

'token': 次の無効な ' ~' (識別子が必要です)

トークンは、識別子ではありません。

次の例では、C2611 が生成されます。

```
// C2611.cpp
// compile with: /c
class C {
   C::~operator int();   // C2611
   ~C();   // OK
};
```