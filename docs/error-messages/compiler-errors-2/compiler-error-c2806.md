---
title: コンパイラ エラー C2806 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2806
dev_langs:
- C++
helpviewer_keywords:
- C2806
ms.assetid: 7c9ff1f4-1590-4c47-991d-b1075a173b48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01cf48170c8fc8b73f9c4cbe36c051a8daff4314
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043639"
---
# <a name="compiler-error-c2806"></a>コンパイラ エラー C2806

'operator 演算子' が仮パラメーターが多すぎます

オーバー ロードされた演算子は、パラメーターが多すぎます。

次の例では、C2806 が生成されます。

```
// C2806.cpp
// compile with: /c
class X {
public:
   X operator++ ( int, int );   // C2806 more than 1 parameter
   X operator++ ( int );   // OK
} ;
```