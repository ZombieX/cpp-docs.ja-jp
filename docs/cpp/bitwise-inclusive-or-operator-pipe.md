---
title: 'ビット処理包括的 OR 演算子: | |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda159ed4111bffe935d5ceb6824662159553ddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032017"
---
# <a name="bitwise-inclusive-or-operator-"></a>ビット処理包括的 OR 演算子: |

## <a name="syntax"></a>構文

> *expression1* **|** *expression2*

## <a name="remarks"></a>Remarks

ビットごとの包括的 OR 演算子 (**&#124;**)、最初のオペランドを 2 番目のオペランドの対応するビットの各ビットと比較します。 どちらかのビットが 1 の場合、対応する結果のビットは 1 に設定されます。 それ以外の場合は、対応する結果ビットが 0 に設定されます。

ビットごとの包括的 OR 演算子のオペランドは両方とも整数型である必要があります。 通常の算術変換は、「[標準変換](standard-conversions.md)オペランドに適用されます。

## <a name="operator-keyword-for-124"></a>演算子キーワード&#124;

**Bitor**演算子と等価のテキストは、  **&#124;** します。 アクセスする 2 つの方法がある、 **bitor**演算子をプログラムで: ヘッダー ファイルをインクルード\<iso646.h > を使用してコンパイル、 [/Za](../build/reference/za-ze-disable-language-extensions.md) (言語拡張を無効にする) コンパイラ オプション。

## <a name="example"></a>例

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>関連項目

[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C ビット処理演算子](../c-language/c-bitwise-operators.md)