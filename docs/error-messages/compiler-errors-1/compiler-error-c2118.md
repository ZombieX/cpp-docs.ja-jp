---
title: コンパイラ エラー C2118 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2118
dev_langs:
- C++
helpviewer_keywords:
- C2118
ms.assetid: bf4315d0-f085-4323-b813-96ee61a13bde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91e79e396f707dc1462b17d9dd470527f199ad10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081638"
---
# <a name="compiler-error-c2118"></a>コンパイラ エラー C2118

負の添字

配列のサイズを定義する値は、配列の最大サイズより大きいまたは 0 より小さい。

次の例では、C2118 が生成されます。

```
// C2118.cpp
int main() {
   int array1[-1];   // C2118
   int array2[3];   // OK
}
```