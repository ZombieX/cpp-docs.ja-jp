---
title: コンパイラ エラー C2192 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2192
dev_langs:
- C++
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6cea2b4ce805c8f7d966ee9d2b3c27f8a901c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023515"
---
# <a name="compiler-error-c2192"></a>コンパイラ エラー C2192

パラメーター 'number' の宣言と異なります。

C の関数は、異なるパラメーター リストで、2 回目で宣言されました。 C では、オーバー ロードされた関数はサポートされません。

次の例に C2192 が生成されます。

```
// C2192.c
// compile with: /Za /c
void func( float, int );
void func( int, float );   // C2192, different parameter list
void func2( int, float );   // OK
```