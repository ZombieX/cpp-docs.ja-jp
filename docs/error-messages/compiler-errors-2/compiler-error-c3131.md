---
title: コンパイラ エラー C3131 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3131
dev_langs:
- C++
helpviewer_keywords:
- C3131
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7830e5c0ea57a7b6b6e42f020f723f1c4f80a7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035488"
---
# <a name="compiler-error-c3131"></a>コンパイラ エラー C3131

プロジェクトが、'module' 属性 'name' プロパティがあります。

[モジュール](../../windows/module-cpp.md)属性には、名前のパラメーターが必要です。

次の例では、C3131 が生成されます。

```
// C3131.cpp
[emitidl];
[module];   // C3131
// try the following line instead
// [module (name="MyLib")];

[public]
typedef long int LongInt;
```