---
title: コンパイラの警告 (レベル 1) C4624 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4624
dev_langs:
- C++
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbc482fe693da366a3ba3ce7e53d5e8bbf23618c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118391"
---
# <a name="compiler-warning-level-1-c4624"></a>コンパイラの警告 (レベル 1) C4624

'derived class' : 基底クラスのデストラクターへのアクセスまたはその削除ができないため、デストラクターを暗黙的に削除済みとして定義しました

デストラクターは基底クラスでアクセスできないか削除されているため、派生クラスでは生成されません。 スタックにこの型のオブジェクトを作成しようとすると、コンパイル エラーが発生します。

次の例では、C4624 を生成し、その修正方法を示しています。

```
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```