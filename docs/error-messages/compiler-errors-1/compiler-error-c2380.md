---
title: コンパイラ エラー C2380 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2380
dev_langs:
- C++
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4dae59f686a1d2fe9f80a4f3f4c47ea6b7ea2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065479"
---
# <a name="compiler-error-c2380"></a>コンパイラ エラー C2380

'identifier' (コンス トラクターが戻り値の型、または現在のクラス名の再定義は無効な選択か) の前の種類

コンス トラクターは、値を返します。 または、クラス名を再定義します。

次の例では C2326 が生成されます。

```
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```