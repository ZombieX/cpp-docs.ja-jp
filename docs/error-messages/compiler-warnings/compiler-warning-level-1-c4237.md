---
title: コンパイラの警告 (レベル 1) C4237 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4237
dev_langs:
- C++
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca72e4973c71655bc4a891570c6f686304d07eb0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092896"
---
# <a name="compiler-warning-level-1-c4237"></a>コンパイラの警告 (レベル 1) C4237

'keyword' キーワードがサポートされていませんが、将来使用するために予約されています

C++ 仕様のキーワードは、Visual C コンパイラで実装されていませんが、キーワードはユーザー定義の記号として使用できません。

次の例では、C4237 が生成されます。

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```