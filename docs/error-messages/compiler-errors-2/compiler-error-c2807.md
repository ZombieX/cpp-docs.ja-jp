---
title: コンパイラ エラー C2807 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2807
dev_langs:
- C++
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a0f1627e19ad3368ad99559b6b576d165347643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110537"
---
# <a name="compiler-error-c2807"></a>コンパイラ エラー C2807

'operator 演算子' の後置 2 番目の仮パラメーターは 'int' である必要があります。

後置演算子の 2 番目のパラメーターが無効な型です。

次の例では、C2807 が生成されます。

```
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```