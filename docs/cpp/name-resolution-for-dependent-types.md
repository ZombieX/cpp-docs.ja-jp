---
title: 依存する型の名前解決 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c17a29f0287ee25517ed72f1c98caa2d38a96195
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040181"
---
# <a name="name-resolution-for-dependent-types"></a>依存する型の名前解決

使用**typename**の修飾名で指定した修飾名が型を識別するようにコンパイラに指示するテンプレートの定義。 詳細については、次を参照してください。 [typename](../cpp/typename.md)します。

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

依存名の名前検索はテンプレート定義の両方のコンテキストから名前を確認する: 次の例では、このコンテキストが見つかります`myFunction(char)`— とテンプレートのインスタンス化のコンテキスト。Main で次の例では、テンプレートがインスタンス化されます。そのため、`MyNamespace::myFunction`がインスタンス化時点から表示されるより適合として選択されます。 `MyNamespace::myFunction` の名前を変更した場合、`myFunction(char)` が代わりに呼び出されます。

すべての名前は依存名のように解決されます。 いずれにしても、名前の衝突が発生する可能性がある場合は、完全修飾名を使用することをお勧めします。

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>出力

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>テンプレートのあいまいさの解消

Visual Studio 2012 では、c++ 98/03/11 標準の規則"template"キーワードで曖昧性除去を適用します。 次の例では、Visual C 2010 は準拠していない行と準拠している行の両方を受け入れるとします。  Visual Studio 2012 では、準拠している行のみを受け入れます。

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

あいまいさを解消する規則に準拠している必要があるのは、既定で、C++ は `AY::Rebind` がテンプレートでないと仮定し、そのためコンパイラは次の "`<`" を "より小さい" と解釈するためです。 "`Rebind`" を山かっことして正しく解析できるように、`<` がテンプレートであることを知っている必要があります。

## <a name="see-also"></a>関連項目

[名前解決](../cpp/templates-and-name-resolution.md)