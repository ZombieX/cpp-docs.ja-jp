---
title: コンパイラ エラー C3804 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3804
dev_langs:
- C++
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef798ec8697ee9a856162b9aa63ccbf23db15f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113202"
---
# <a name="compiler-error-c3804"></a>コンパイラ エラー C3804

'property_accessor': アクセサー メソッドをプロパティには、いずれかが必要がありますはすべて静的、またはすべてスタティックでないです。

アクセサー関数が静的にできる非 trivial プロパティを定義するときにインスタンスが両方のか。

詳細については、「 [property](../../windows/property-cpp-component-extensions.md) 」を参照してください。

## <a name="example"></a>例

次の例では、C3804 が生成されます。

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```