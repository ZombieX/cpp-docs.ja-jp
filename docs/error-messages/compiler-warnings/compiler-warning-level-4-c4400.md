---
title: コンパイラの警告 (レベル 4) C4400 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd22db0313d2d0ea6494908259e7d098336f6dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016196"
---
# <a name="compiler-warning-level-4-c4400"></a>コンパイラの警告 (レベル 4) C4400

'type': この型での const/volatile 修飾子はサポートされていません

[Const](../../cpp/const-cpp.md)と[揮発性](../../cpp/volatile-cpp.md)修飾子は、共通言語ランタイム型の変数では動作しません。

## <a name="example"></a>例

次の例では、C4400 が生成されます。

```
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```