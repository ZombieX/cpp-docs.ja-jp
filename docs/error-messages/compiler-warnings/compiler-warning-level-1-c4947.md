---
title: コンパイラの警告 (レベル 1) C4947 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4947
dev_langs:
- C++
helpviewer_keywords:
- C4947
ms.assetid: 5a1d484e-b4c7-4de2-a145-d8dcfc2fc1d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fccb30128392c5e6de12f33f58e207502643e002
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050451"
---
# <a name="compiler-warning-level-1-c4947"></a>コンパイラの警告 (レベル 1) C4947

'type_or_member': 廃止としてマークされています

メンバーまたは型が、 <xref:System.ObsoleteAttribute> クラスで obsolete としてマークされています。

## <a name="example"></a>例

次の例では C4947 が生成されます。

```cpp
// C4947.cpp
// compile with: /clr /W1
// C4947 expected
using namespace System;

[System::ObsoleteAttribute]
ref struct S {
   [System::ObsoleteAttribute]
   int i;

   [System::ObsoleteAttribute]
   void mFunc(){}
};

// Any reference to Func1 should generate a warning
[System::ObsoleteAttribute]
Int32 Func1(Int32 a, Int32 b) {
   return (a + b);
}

// Any reference to Func2 should generate a warning with  message
[System::ObsoleteAttribute("Will be removed in next version")]
Int32 Func2(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt1 = ::Func1(2, 2);
   Int32 MyInt2 = ::Func2(2, 2);

   S^ s = gcnew S();
   s->i = 10;
   s->mFunc();
}
```