---
title: コンパイラの警告 (レベル 1) C4083 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4083
dev_langs:
- C++
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64e81b6a68a9584e4fb30829e15da6472212ce05
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046369"
---
# <a name="compiler-warning-level-1-c4083"></a>コンパイラの警告 (レベル 1) C4083

'token' が必要です。識別子 'identifier' が見つかりました

間違った場所に識別子が発生した、 **#pragma**ステートメント。

## <a name="example"></a>例

```
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

構文チェック、 [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)ディレクティブ。