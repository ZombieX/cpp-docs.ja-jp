---
title: コンパイラの警告 (レベル 4) C4429 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4429
dev_langs:
- C++
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19e10806ffa601caa4212b5e5f98b823ec8941d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049229"
---
# <a name="compiler-warning-level-4-c4429"></a>コンパイラの警告 (レベル 4) C4429

考えられる不完全または形式の正しくないユニバーサル文字名

正しくない形式のユニバーサル文字名を使用できる文字シーケンスが検出されました。 ユニバーサル文字名は`\u`4 つの 16 進数字が続くまたは`\U`8 つの 16 進数字が続きます。

次の例では、C4429 が生成されます。

```
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```