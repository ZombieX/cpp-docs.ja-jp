---
title: コンパイラ エラー C3458 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3458
dev_langs:
- C++
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5564f944fdebb15292620c7ada882633aa3e671
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090374"
---
# <a name="compiler-error-c3458"></a>コンパイラ エラー C3458

'attribute1': 'construct' に対して属性 'attribute2' は既に指定されています

相互に排他的である 2 つの属性が、同じコンストラクトに指定されました。

## <a name="example"></a>例

次の例では C3458 が生成されます。

```
// C3458.cpp
// compile with: /clr /c
[System::Reflection::DefaultMember("Chars")]
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458
   property char default[int] {
      char get(int index);
      void set(int index, char c);
   }
};
```