---
title: コンパイラの警告 (レベル 1) C4346 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4346
dev_langs:
- C++
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49e749ac4878098cf3800915de4838285150c2fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024841"
---
# <a name="compiler-warning-level-1-c4346"></a>コンパイラの警告 (レベル 1) C4346

'name': 依存名が型ではありません

[Typename](../../cpp/typename.md)依存名が型として扱われる場合は、キーワードが必要です。 すべてのバージョンの Visual C で同様に動作するコードの場合は、追加`typename`宣言にします。

次の例では、C4346 が生成されます。

```
// C4346.cpp
// compile with: /WX /LD
template<class T>
struct C {
   T::X* x;   // C4346
   // try the following line instead
   // typename T::X* x;
};
```

次のサンプルは、その他の例を示しています。 場所、 **typename**キーワードが必要です。

```
// C4346b.cpp
// compile with: /LD /W1
template<class T>
const typename T::X& f(typename T::Z* p);   // Required in both places

template<class T, int N>
struct L{};

template<class T>
struct M : public L<typename T::Type, T::Value>
{   // required on type argument, not on non-type argument
   typedef typename T::X   Type;
   Type f();   // OK: "Type" is a type-specifer
   typename T::X g();   // typename required
   operator typename T::Z();   // typename required
};
```

でこれを

```
// C4346c.cpp
// compile with: /LD /WX
struct Y {
   typedef int Y_t;
};

template<class T>
struct A {
   typedef Y A_t;
};

template<class T>
struct B {
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here
};
```