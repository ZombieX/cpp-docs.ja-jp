---
title: コンパイラ エラー C3749 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3749
dev_langs:
- C++
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ac866d742734f5b6126315a0b79020c9ec7fb74
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788397"
---
# <a name="compiler-error-c3749"></a>コンパイラ エラー C3749

'attribute': 関数内で、カスタム属性を使用しない場合があります

カスタム属性は、関数内で使用できません。 カスタム属性の詳細については、トピックを参照してください。[属性](../../windows/attributes/attribute.md)します。

## <a name="example"></a>例

次の例では、C3749 が生成されます。

```
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
