---
title: constexpr (C++) |Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 150179fc0fd97450ba805d6957f5282bfaf8345c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071259"
---
# <a name="constexpr-c"></a>constexpr (C++)

キーワード**constexpr** c++ 11 で導入され、c++ 14 で改良されました。 意味*定数式*します。 ような**const**値を変更しようとしているすべてのコードと、コンパイラ エラーが発生するためには、変数に適用することができます。 異なり**const**、 **constexpr**関数に適用することもでき、クラスのコンス トラクター。 **constexpr**ことを示します値、または戻り値は、定数、可能であれば、コンパイル時に計算されます。

A **constexpr** const の整数がテンプレート引数や配列の宣言など、必要な整数値を使用できます。 値は、実行時ではなくコンパイル時に計算することができます、ときに実行速度が向上しより少ないメモリを使用して、プログラムに役立ちます。

定数式に含まれる型に制限することが標準の c++ 14 コンピューティングのコンパイル時定数の複雑さと、コンパイル時の潜在的な影響を制限するため必要[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)します。

## <a name="syntax"></a>構文

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>パラメーター

*params*<br/>
リテラル型である必要がありますし、それ自体をする必要があります、1 つまたは複数のパラメーターには、定数式があります。

## <a name="return-value"></a>戻り値

Constexpr 変数または関数が返す必要があります、[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)します。

## <a name="constexpr-variables"></a>constexpr 変数

const 変数と constexpr 変数の主な違いとして、const 変数の初期化は実行時まで遅延できるのに対し、constexpr 変数はコンパイル時に初期化する必要があります。  すべての constexpr 変数は、const です。

- 変数を宣言することができます**constexpr**、リテラルの型と初期化されます。 コンス トラクターによって初期化が実行される場合、コンス トラクターとして宣言する必要があります**constexpr**します。

- 参照するオブジェクトが定数式で初期化され、初期化中に呼び出される暗黙の変換もすべて定数式である場合には、参照を constexpr と宣言することができます。

- すべての宣言を**constexpr**変数または関数が必要、 **constexpr**指定子。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> constexpr 関数

A **constexpr**関数は、1 つの要求コードを実行されたときにコンパイル時の戻り値を計算することができます。  ときに、引数が**constexpr**値、および使用側コードを初期化する例については、コンパイル時に、戻り値が必要です、 **constexpr**変数を非型テンプレート引数を指定または、コンパイル時定数を生成します。 以外で呼び出されたときに**constexpr**引数で正規関数のように実行時に値を生成、その値がコンパイル時に必要な場合は、または。  (この 2 重の動作と記述する手間が省けます**constexpr**と非-**constexpr**同じ関数のバージョン)。

A **constexpr**関数またはコンス トラクターは暗黙的に**インライン**します。

Constexpr 関数に次の規則が適用されます。

- A **constexpr**関数がそのまま使用する必要があり、のみを返します[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)します。

- A **constexpr**関数が再帰的なをすることができます。

- できません[仮想](../cpp/virtual-cpp.md)します。 場合は、外側のクラスがある仮想基底クラス コンス トラクターは constexpr として定義できません。

- 本体は `= default` または `= delete` として定義できます。

- 本文を含まない**goto**ステートメントまたはブロックをお試しください。

- Constexpr ではないテンプレートの明示的な特殊化として宣言できます**constexpr**:

- 明示的な特殊化を**constexpr**テンプレートがあることがありません**constexpr**:

次の規則に適用されます**constexpr** Visual Studio 2017 以降の機能。

- いる可能性がある**場合**と**スイッチ**ステートメント、およびすべてのループ ステートメントを含む**の**、範囲に基づく、**中**、および**は-中**します。

- ローカル変数の宣言を含めることができますが、変数の初期化する必要があります、リテラルの型である必要があります、および静的あるいはスレッド ローカルにすることはできません。 ローカルに宣言された変数は const を指定する必要はありませんし、変更可能性があります。

- Constexpr の非静的メンバー関数は、暗黙的に const を指定する必要はありません。

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 注: Visual Studio デバッガーで、ビルドをデバッグする非最適化をデバッグするを区別するかどうかを**constexpr**関数は、内部にブレークポイントを設定することによってコンパイル時に評価されるは。 ブレークポイントにヒットすると、実行時に関数が呼び出されます。  ヒットしなければ、コンパイル時に関数が呼び出されます。

## <a name="extern-constexpr"></a>extern constexpr

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md)コンパイラ オプションは、適用するコンパイラ[外部リンケージ]()を使用して宣言された変数に**extern constexpr**します。 以前のバージョンの Visual Studio で、既定の場合、または **/Zc:externConstexpr-** を指定すると、Visual Studio に内部リンケージを適用する**constexpr**変数場合でも、 **extern**キーワードを使用します。 **/Zc: externconstexpr**オプションは、Visual Studio 2017 Update 15.6 以降を使用します。 既定で無効であるとします。 促す/permissive-オプションには、/zc: externconstexpr が有効にしません。

## <a name="example"></a>例

次の例は**constexpr**変数、関数、およびユーザー定義の型。 なお、main() の最後のステートメントで、 **constexpr**値がコンパイル時に既知である必要はないために、メンバー関数 GetValue() は実行時の呼び出し。

```cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile time computation of array length
template<typename T, int N>
constexpr int length(const T(&ary)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n*fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue()
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    //foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    //Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    //Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;

}
```

## <a name="requirements"></a>必要条件

Visual Studio 2015

## <a name="see-also"></a>関連項目

[宣言と定義](../cpp/declarations-and-definitions-cpp.md)<br/>
[const](../cpp/const-cpp.md)
