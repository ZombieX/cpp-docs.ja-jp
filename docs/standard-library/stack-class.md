---
title: stack クラス | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
dev_langs:
- C++
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 166a0fe22669927e0b57f56fae61847eb950537f
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861526"
---
# <a name="stack-class"></a>stack クラス

基になるコンテナー型に最も新しく追加された要素へのアクセスを制限することにより、機能の制限を提供するテンプレート コンテナーのアダプター クラスです。 stack クラスは、スタック操作のみがコンテナーで実行されることが明確であることが重要な場合に使用されます。

## <a name="syntax"></a>構文

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>パラメーター

*Type*<br/>
スタックに格納される要素のデータ型。

*コンテナー*<br/>
スタックを実装するために使用する基になるコンテナーの型。 既定値は、クラス `deque`*\<Type>* です。

## <a name="remarks"></a>Remarks

クラスの要素`Type`最初のテンプレートで規定されているパラメーターのスタック オブジェクト[value_type](#value_type)と基になるコンテナー クラス内の要素の型に一致する必要があります`Container`によって規定、2 番目のテンプレート パラメーター。 `Type`その型のオブジェクトをコピーして、その型の変数に値を割り当てることができるように、割り当てることがあります。

スタックに適した基になるコンテナー クラスを含める[deque](../standard-library/deque-class.md)、 [list クラス](../standard-library/list-class.md)、および[vector クラス](../standard-library/vector-class.md)、またはの操作をサポートするその他のすべてのシーケンス コンテナー`back`、 `push_back`、および`pop_back`します。 基になるコンテナー クラスは、コンテナー アダプター内にカプセル化されます。コンテナー アダプターは、限られた一連のシーケンス コンテナーのメンバーの関数のみをパブリック インターフェイスとして公開します。

Stack オブジェクトは、等値比較できる場合、場合にのみをクラスの要素は`Type`は等しいかどうかを比較し、小さい-なり場合にのみ、クラスの要素`Type`小さい-比較対象より。

- stack クラスは、後入れ先出し (LIFO) のデータ構造をサポートしています。 思い描くのに助けとなるのは、積み重ねられた皿です。 要素 (皿) は、積み重ねの一番上からのみ挿入、検査、または削除できます。積み重ねの一番上に相当するのは、基本のコンテナーの末尾にある最後の要素です。 一番上の要素にのみアクセスできる制限があることが、stack クラスを使用する理由です。

- [queue クラス](../standard-library/queue-class.md)は、先入れ先出し (FIFO) のデータ構造をサポートしています。 思い描くのに助けとなるのは、銀行の窓口で並んでいる人です。 要素 (人々) は、列の一番後ろに追加され、列の一番前から取り除くことができます。 列の一番前と一番後ろの両方を検査できます。 このように一番前と一番後ろの要素にのみアクセスできる制限があることが、queue クラスを使用する理由です。

- [Priority_queue クラス](../standard-library/priority-queue-class.md)は、最も大きな要素が常に先頭の位置になるように、その要素を並べ替えます。 要素の挿入、および先頭の要素の検査と削除をサポートしています。 思い描くのに助けとなるのは、年齢、身長、またはその他の条件によって整列している人です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[stack](#stack)|空であるか、基本のコンテナー オブジェクトのコピーである `stack` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[container_type](#container_type)|`stack` によって適合されるように、基本のコンテナーを提供する型。|
|[size_type](#size_type)|`stack` 内の要素の数を表すことができる符号なし整数型。|
|[value_type](#value_type)|`stack` 内に要素として格納されるオブジェクトの種類を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[empty](#empty)|`stack` が空かどうかをテストします。|
|[pop](#pop)|`stack` の先頭から要素を削除します。|
|[push](#push)|`stack` の先頭に要素を追加します。|
|[size](#size)|`stack` 内の要素数を返します。|
|[top](#top)|`stack` の先頭にある要素への参照を返します。|

## <a name="requirements"></a>要件

**ヘッダー:** \<stack>

**名前空間:** std

## <a name="container_type"></a>  stack::container_type

適合されるように、基本のコンテナーを提供する型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Container` のシノニムです。 3 つの C++ 標準ライブラリ シーケンス コンテナー クラス (vector クラス、list クラス、既定の deque クラス) はすべて、stack オブジェクトの基本のコンテナーとしての使用要件を満たしています。 こうした要件を満たすユーザー定義型を使用することもできます。

`Container`の詳細については、[stack クラス](../standard-library/stack-class.md)のトピックのコメントに関するセクションを参照してください。

### <a name="example"></a>例

`container_type` の宣言方法や使用方法の例については、[stack::stack](#stack) の例を参照してください。

## <a name="empty"></a>  stack::empty

stack が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

set が空の場合は **true**、set が空ではない場合は **false**。

### <a name="example"></a>例

```cpp
// stack_empty.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack <int> s1, s2;

   s1.push( 1 );

   if ( s1.empty( ) )
      cout << "The stack s1 is empty." << endl;
   else
      cout << "The stack s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The stack s2 is empty." << endl;
   else
      cout << "The stack s2 is not empty." << endl;
}
```

```Output
The stack s1 is not empty.
The stack s2 is empty.
```

## <a name="pop"></a>  stack::pop

stack の先頭から要素を削除します。

```cpp
void pop();
```

### <a name="remarks"></a>Remarks

メンバー関数を適用するには、stack を空にすることはできません。 stack の先頭は最も直近に追加された要素によって占有される位置であり、コンテナーの末尾にある最後の要素になります。

### <a name="example"></a>例

```cpp
// stack_pop.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;

   s1.pop( );

   i = s1.size( );
   cout << "After a pop, the stack length is "
        << i << "." << endl;

   i = s1.top( );
   cout << "After a pop, the element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
After a pop, the stack length is 2.
After a pop, the element at the top of the stack is 20.
```

## <a name="push"></a>  stack::push

スタックの先頭に要素を追加します。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>パラメーター

*val*<br/>
スタックの先頭に追加される要素。

### <a name="remarks"></a>Remarks

stack の先頭は最も直近に追加された要素によって占有される位置であり、コンテナーの末尾にある最後の要素になります。

### <a name="example"></a>例

```cpp
// stack_push.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
```

## <a name="size"></a>  stack::size

stack 内の要素数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

stack の現在の長さ。

### <a name="example"></a>例

```cpp
// stack_size.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;
   stack <int>::size_type i;

   s1.push( 1 );
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   s1.push( 2 );
   i = s1.size( );
   cout << "The stack length is now " << i << "." << endl;
}
```

```Output
The stack length is 1.
The stack length is now 2.
```

## <a name="size_type"></a>  stack::size_type

stack 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Remarks

この型は、stack によって採用された基本コンテナーの `size_type` のシノニムです。

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[size](#size) の例を参照してください。

## <a name="stack"></a>  stack::stack

空であるか、基本のコンテナー クラスのコピーである stack を構築します。

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
構築される container のコピー元となる container。

### <a name="example"></a>例

```cpp
// stack_stack.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stack with default deque base container
   stack <char> dsc1;

   //Explicitly declares a stack with deque base container
   stack <char, deque<char> > dsc2;

   // Declares a stack with vector base containers
   stack <int, vector<int> > vsi1;

   // Declares a stack with list base container
   stack <int, list<int> > lsi;

   // The second member function copies elements from a container
   vector<int> v1;
   v1.push_back( 1 );
   stack <int, vector<int> > vsi2( v1 );
   cout << "The element at the top of stack vsi2 is "
        << vsi2.top( ) << "." << endl;
}
```

```Output
The element at the top of stack vsi2 is 1.
```

## <a name="top"></a>  stack::top

stack の先頭にある要素への参照を返します。

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>戻り値

stack の先頭にあるコンテナーの最後の要素への参照。

### <a name="remarks"></a>Remarks

メンバー関数を適用するには、stack を空にすることはできません。 stack の先頭は最も直近に追加された要素によって占有される位置であり、コンテナーの末尾にある最後の要素になります。

場合の戻り値`top`に割り当てられている、 `const_reference`、stack オブジェクトは変更できません。 場合の戻り値`top`に割り当てられている、 `reference`、stack オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// stack_top.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 1 );
   s1.push( 2 );

   int& i = s1.top( );
   const int& ii = s1.top( );

   cout << "The top integer of the stack s1 is "
        << i << "." << endl;
   i--;
   cout << "The next integer down is "<< ii << "." << endl;
}
```

```Output
The top integer of the stack s1 is 2.
The next integer down is 1.
```

## <a name="value_type"></a>  stack::value_type

stack 内に要素として格納されるオブジェクトの種類を表す型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Remarks

この型は、stack によって採用された基本コンテナーの `value_type` のシノニムです。

### <a name="example"></a>例

```cpp
// stack_value_type.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   stack<int> s1;
   s1.push( AnInt );
   cout << "The element at the top of the stack is "
        << s1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the stack is 69.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)<br/>
