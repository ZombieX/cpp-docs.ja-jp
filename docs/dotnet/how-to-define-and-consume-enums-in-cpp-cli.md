---
title: '方法: 定義および c++ の列挙型を使用する/cli CLI |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b1d7d7c98b7827f91102704e2fd3c1325a66d36b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431746"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>方法: C++/CLI で列挙型を定義および使用する

このトピックでは、c++ の列挙型を説明/cli CLI。

## <a name="specifying-the-underlying-type-of-an-enum"></a>Enum の基になる型を指定します。

列挙体の基になる型は、既定では、`int`します。  ただし、ある符号付きまたは符号なしの形式の種類を指定できます`int`、 `short`、 `long`、 `__int32`、または`__int64`します。  使用することも`char`します。

```
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**出力**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>マネージ コードと標準列挙型の間で変換する方法

列挙型と整数型以外の標準変換はありません。キャストが必要です。

```
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**出力**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>演算子と列挙型

次の演算子は C で列挙型で有効な/cli CLI:

|演算子|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

演算子&#124;^ & ~ +-ブール値を含まない型の基になる整数型と列挙型に対してのみ定義されます。  列挙型の両方のオペランドがあります。

列挙操作の結果のチェックを静的または動的なコンパイラがしません操作は、列挙型の有効な列挙子の範囲にない値があります。

> [!NOTE]
>  C++ 11 に c++ のマネージ列挙型クラスよりも大幅に異なるアンマネージ コードで列挙型のクラス型が導入されています/cli CLI。 具体的には、c++ 11 enum クラス型はサポートしていませんマネージ列挙型クラスの型として同じ演算子 c++/cli CLI、および C++/cli CLI のソース コードする必要がありますマネージ列挙型では、アクセシビリティ指定子クラスを宣言するアンマネージ (C++ と区別できるようにするには11) 列挙型クラスの宣言。 C++ enum クラスの詳細については/cli CLI、C +/cli/CX、および c++ 11 を参照してください。[列挙型クラス](../windows/enum-class-cpp-component-extensions.md)します。

```
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**出力**

```Output
4
1
True
```

## <a name="see-also"></a>関連項目

[列挙型クラス](../windows/enum-class-cpp-component-extensions.md)