---
title: コンパイラ エラー C3227 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3227
dev_langs:
- C++
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddf2ec945a8bdbe103631d8346641e1370eda216
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096627"
---
# <a name="compiler-error-c3227"></a>コンパイラ エラー C3227

'parameter': 'keyword' を使用して、ジェネリック型を割り当てることはできません

型をインスタンス化するために適切なコンス トラクターが必要です。 ただし、コンパイラでは、適切なコンス トラクターが使用できることを確認することはありません。

ジェネリックではなくテンプレートを使用するには、このエラーを解決するのには、またはいくつかのメソッドのいずれかを使用して、型のインスタンスを作成することができます。

## <a name="example"></a>例

次の例では、C3227 が生成されます。

```
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```