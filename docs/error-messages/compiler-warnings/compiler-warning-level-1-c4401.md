---
title: コンパイラの警告 (レベル 1) C4401 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4401
dev_langs:
- C++
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f9f7bfcf826b9bda4232a8f4068d8be45dc3ab5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043548"
---
# <a name="compiler-warning-level-1-c4401"></a>コンパイラの警告 (レベル 1) C4401

'ビット フィールド': メンバーがビット フィールドです

インライン アセンブリ コードは、ビット フィールド メンバーにアクセスしようとします。 ビット フィールド メンバーの前に最後のパッキング境界が使用されるため、インライン アセンブリは、ビット フィールド メンバーにアクセスできません。

この警告を回避するには、インライン アセンブリ コード内の参照を行う前に適切な型をビット フィールドをキャストします。 次の例では、C4401 が生成されます。

```
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```