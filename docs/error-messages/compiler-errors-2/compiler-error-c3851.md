---
title: コンパイラ エラー C3851 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6d0f6da9c3295aa6a8fad4bf5dfd8e725424739
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032489"
---
# <a name="compiler-error-c3851"></a>コンパイラ エラー C3851

> '*char*': ユニバーサル文字名は基本文字セット内の文字を指定できません

## <a name="remarks"></a>Remarks

C++ としてコンパイルされるコードでは、基本ソース文字セットの文字を表すユニバーサル文字名を使用できません (文字列リテラルまたは文字リテラルの場合を除く)。 詳細については、次を参照してください。[文字セット](../../cpp/character-sets.md)します。 C としてコンパイルされたコードで使うことはできません、ユニバーサル文字名を範囲 0x20 から 0x7f、0x24 ('$') を除く、包括的で 0x40 ('\@')、または 0x60 ('\`')。

## <a name="example"></a>例

次の例では、C3851 が生成され、その修正方法が表示されます。

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```