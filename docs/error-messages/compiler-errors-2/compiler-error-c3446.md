---
title: コンパイラ エラー C3446 |Microsoft Docs
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a88bb77489d2596c271842e7becb0214d1af2821
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018868"
---
# <a name="compiler-error-c3446"></a>コンパイラ エラー C3446

>'*クラス*': 値クラスのメンバーの既定のメンバー初期化子は許可されていません

Visual Studio 2015 以前では、コンパイラは、値クラスのメンバーの既定のメンバーの初期化子を許可しました (ただし無視しました)。 値クラスの既定の初期化子は、常にメンバーを 0 に初期化します。既定のコンストラクターは許可されません。 Visual Studio 2017 年では、この例に示すように、既定メンバー初期化子は、コンパイラ エラーを発生させます。

## <a name="example"></a>例

次の例では、Visual Studio 2017 以降 C3446 が生成されます。

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

エラーを修正するには、初期化子を削除します。

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

