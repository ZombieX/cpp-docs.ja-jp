---
title: コンパイラ エラー C3279 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89c537da9bcf91e7774353cc1516a4c44e28649c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056769"
---
# <a name="compiler-error-c3279"></a>コンパイラ エラー C3279

cli 名前空間で宣言されたクラス テンプレートの明示的なインスタンス生成と同様に、部分的または明示的な特殊化は許可されていません

`cli` 名前空間は、Microsoft によって定義され、擬似テンプレートが含まれています。 Visual C++ コンパイラでは、この名前空間におけるユーザー定義、部分的、および明示的な特殊化は許可されず、クラス テンプレートの明示的なインスタンス化も許可されません。

次の例では C3279 が生成されます。

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```