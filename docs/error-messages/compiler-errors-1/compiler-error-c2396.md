---
title: コンパイラ エラー C2396 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d69dfc1e296532f00ce9f44a178a366dca41e2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061631"
---
# <a name="compiler-error-c2396"></a>コンパイラ エラー C2396

' your_type::operator'type ': 有効な CLR または WinRT のユーザー定義の変換 functionnot します。 変換元または変換先が次の値でなければなりません: 'T^'、'T^%'、'T^&' (ここで T = 'your_type')

Windows ランタイム型またはマネージド型の変換関数に、変換関数が含まれる型と同じ型を持つ 1 つ以上のパラメーターがありません。

次の例では、C2396 を生成し、その修正方法を示しています。

```
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```