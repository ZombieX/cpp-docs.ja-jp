---
title: コンパイラ エラー C3417 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3417
dev_langs:
- C++
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b21636c3500625f262355750d32aa0fa3faeb5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073851"
---
# <a name="compiler-error-c3417"></a>コンパイラ エラー C3417

'member': 値型は、特殊なメンバーのユーザー定義関数を含めることはできません

値型では、既定のインスタンス コンス トラクター、デストラクター、またはコピー コンス トラクターなどの関数を含めることはできません。

次の例では、c3517 エラーが生成されます。

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```