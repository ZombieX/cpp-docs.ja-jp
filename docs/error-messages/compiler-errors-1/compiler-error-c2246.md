---
title: コンパイラ エラー C2246 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2246
dev_langs:
- C++
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c605d6cdf30a4c184e59627ddc3819812c290d68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029092"
---
# <a name="compiler-error-c2246"></a>コンパイラ エラー C2246

'identifier': ローカルに定義されたクラスの静的データ メンバーが正しくありません

ローカル スコープのクラス、構造体、共用体のメンバーが `static`で宣言されています。

次の例では C2246 が生成されます。

```
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```