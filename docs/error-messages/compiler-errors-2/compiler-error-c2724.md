---
title: コンパイラ エラー C2724 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2724
dev_langs:
- C++
helpviewer_keywords:
- C2724
ms.assetid: 4e4664bc-8c96-4156-b79f-03436f532ea8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d637892a71f9a2c9bafdced6cb3a6e51e23ae463
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029339"
---
# <a name="compiler-error-c2724"></a>コンパイラ エラー C2724

'identifier': 'static' する必要がありますでは使用できませんファイル スコープで定義されているメンバー関数

静的メンバー関数は、外部リンケージで宣言する必要があります。

次の例では、C2724 が生成されます。

```
// C2724.cpp
class C {
   static void func();
};

static void C::func(){};   // C2724
// try the following line instead
// void C::func(){};
```