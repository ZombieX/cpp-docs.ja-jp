---
title: コンパイラ エラー C3062 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f2e58cada0b1b825fb0f065b461db6350de9fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067169"
---
# <a name="compiler-error-c3062"></a>コンパイラ エラー C3062

'enum': 基になる型は 'type' であるために、列挙子から値が必要です

列挙体は、基になる型を指定することができます。 ただし、一部の種類には、列挙子ごとに値を代入する必要があります。

列挙型の詳細については、次を参照してください。[列挙型クラス](../../windows/enum-class-cpp-component-extensions.md)します。

次の例では、C3062 が生成されます。

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```