---
title: コンパイラ エラー C2171 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2171
dev_langs:
- C++
helpviewer_keywords:
- C2171
ms.assetid: a80343b5-ab3f-4413-b6f1-3ce9d7e519e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5c2e3c87db5a82cc3606ebca049a35adec5fa61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029248"
---
# <a name="compiler-error-c2171"></a>コンパイラ エラー C2171

'operator': 型 'type' のオペランドが無効です

単項演算子が無効なオペランド型で使用されています。

## <a name="example"></a>例

次の例では C2171 が生成されます。

```
// C2171.cpp
int main() {
   double d, d1;
   d = ~d1;   // C2171

   // OK
   int d2 = 0, d3 = 0;
   d2 = ~d3;
}
```

## <a name="example"></a>例

次の例では C2171 が生成されます。

```
// C2171_b.cpp
// compile with: /c
class A {
public:
   A() { STF( &A::D ); }

   void D() {}
   void DTF() {
      (*TF)();   // C2171
      (this->*TF)();   // OK
   }

   void STF(void (A::*fnc)()) {
      TF = fnc;
   }

private:
   void (A::*TF)();
};
```