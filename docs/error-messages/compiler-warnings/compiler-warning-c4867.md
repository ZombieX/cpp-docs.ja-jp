---
title: コンパイラの警告 C4867 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b444156ae87e43b068521a3ad6687abe71df293f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074319"
---
# <a name="compiler-warning-c4867"></a>コンパイラの警告 C4867

'function': 関数呼び出しの引数リストがありません。'call' を使用して、メンバーへのポインターを作成するには

メンバー関数へのポインターが正しく初期化されていません。

この警告は、Visual C 2005 で行ったコンパイラ準拠作業の結果として生成できます。 準拠が強化されたメンバーへのポインター。  Visual C 2005 より前にコンパイルされたコードには、今すぐ C4867 が生成されます。

この警告は、常にエラーとして表示されます。 この警告を無効にするには、 [warning](../../preprocessor/warning.md) プラグマを使用します。 C4867 と MFC と ATL の詳細については、次を参照してください。 [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)します。

## <a name="example"></a>例

次の例では、C4867 が生成されます。

```
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```