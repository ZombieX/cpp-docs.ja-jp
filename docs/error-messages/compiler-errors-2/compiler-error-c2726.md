---
title: コンパイラ エラー C2726 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2726
dev_langs:
- C++
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e421839e75bcc570578d7c37eecc8ab076321d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051273"
---
# <a name="compiler-error-c2726"></a>コンパイラ エラー C2726

'gcnew' は、マネージド型または WinRT 型のオブジェクトの作成にのみ使用できます

ガベージ コレクション ヒープ上でネイティブ型のインスタンスを作成することはできません。

次の例では、C2726 を生成し、その修正方法を示しています。

```
// C2726.cpp
// compile with: /clr
using namespace System;
class U {};
ref class V {};
value class W {};

int main() {
   U* pU = gcnew U;    // C2726
   U* pU2 = new U;   // OK
   V^ p2 = gcnew V;   // OK
   W p3;   // OK

}
```
