---
title: コンパイラ エラー C2893 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73d4f838f030db3667b08295006c2ea1df94c87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026180"
---
# <a name="compiler-error-c2893"></a>コンパイラ エラー C2893

関数テンプレート 'テンプレート名' に失敗しました

コンパイラは、関数テンプレートの特殊化に失敗しました。 このエラーの原因の多くがあります。

一般に、C2893 エラーを解決する方法は、関数のシグネチャを確認し、すべての型をインスタンス化できるかどうかを確認します。

## <a name="example"></a>例

C2893 は、ために発生します。`f`のテンプレート パラメーター`T`があると推測`std::map<int,int>`、が`std::map<int,int>`メンバーを持たない`data_type`(`T::data_type`でインスタンス化できないことができます`T = std::map<int,int>`。)。 次の例では、C2893 が生成されます。

```
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```