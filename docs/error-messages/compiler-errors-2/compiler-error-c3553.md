---
title: コンパイラ エラー C3553 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3553
dev_langs:
- C++
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c91697b8fa4f04c040d92f8af3aa004bbde7a773
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118624"
---
# <a name="compiler-error-c3553"></a>コンパイラ エラー C3553

> decltype には型ではなく式を指定してください

`decltype()` キーワードでは、型の名前ではなく、引数として式を指定する必要があります。 たとえば、次のコード フラグメントの最後のステートメントではエラー C3553 が生成されます。

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```