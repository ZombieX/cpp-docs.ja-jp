---
title: コンパイラ エラー C3554 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b1760607a335d4dd56ec711eef76f5a68550d64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089503"
---
# <a name="compiler-error-c3554"></a>コンパイラ エラー C3554

'decltype' を他の型指定子と組み合わせることはできません

型指定子を使用して `decltype()` キーワードを修飾することはできません。 たとえば、次のコード フラグメントではエラー C3554 が生成されます。

```
int x;
unsigned decltype(x); // C3554
```