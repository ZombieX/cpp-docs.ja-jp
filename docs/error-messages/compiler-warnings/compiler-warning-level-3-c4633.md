---
title: コンパイラの警告 (レベル 3) C4633 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4633
dev_langs:
- C++
helpviewer_keywords:
- C4633
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54a180bcd135f4614fa6cc67cf7647acdfa1c445
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085746"
---
# <a name="compiler-warning-level-3-c4633"></a>コンパイラの警告 (レベル 3) C4633

XML ドキュメント コメント ターゲット: エラー: 理由

渡される、名前、 [ \<param >](../../ide/param-visual-cpp.md)コンパイラによってタグが見つかりません。

次の例では、C4633 が生成されます。

```
// C4633.cpp
// compile with: /clr /doc /LD /W3

/// Text for class MyClass.
public ref class MyClass {
   // C4633 remove line for Int3
   /// <param name="Int1">Used to indicate status.</param>
   /// <param name="Int3">Used to indicate status.</param>
   void MyMethod(int Int1) {
      Int1 = 0;
      Int1++;
   }
};
```