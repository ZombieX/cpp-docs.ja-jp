---
title: コンパイラ エラー C2010 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2010
dev_langs:
- C++
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4be71136d02a563d4dde5d720fe5ae51e0c3c5b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028968"
---
# <a name="compiler-error-c2010"></a>コンパイラ エラー C2010

'character': マクロの仮パラメーター リストで予期しません。

マクロ定義の仮パラメーター リストの中で、文字が正しくない方法で使用されています。 エラーを解決する文字を削除します。

次の例では、C2010 が生成されます。

```
// C2010.cpp
// compile with: /c
#define mymacro(a|) (2*a)   // C2010
#define mymacro(a) (2*a)   // OK
```