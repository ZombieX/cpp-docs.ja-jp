---
title: コンパイラの警告 (レベル 4) C4626 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4626
dev_langs:
- C++
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16ae3e9d9e54d54a419bfde2250fc02f780e8e54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083666"
---
# <a name="compiler-warning-level-4-c4626"></a>コンパイラの警告 (レベル 4) C4626

'derived class' : 基底クラスの代入演算子がアクセスできないか削除されているため、代入演算子は暗黙的に削除済みとして定義されました

代入演算子は基底クラスで削除されているかアクセスできないため、派生クラスでは生成されません。 この型のオブジェクトを代入しようとすると、コンパイラ エラーが発生します。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4626 を生成し、その修正方法を示しています。

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```