---
title: コンパイラ エラー C2570 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2570
dev_langs:
- C++
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5914af21ec780167c45334829a5d6517cf3662
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052986"
---
# <a name="compiler-error-c2570"></a>コンパイラ エラー C2570

'identifier': 共用体は基底クラスを含めることはできません

共用体は、クラス、構造体または共用体から派生します。 これは認められていません。 代わりに、クラスまたは構造体として、派生型を宣言します。

次の例では、C2570 が生成されます。

```
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```