---
title: コンパイラ エラー C2046 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2046
dev_langs:
- C++
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ee043be0a5b7f259f51082c5d48d77b77f0a6db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060071"
---
# <a name="compiler-error-c2046"></a>コンパイラ エラー C2046

'case' が正しくありません。

キーワード `case` は `switch` ステートメントでのみ使用できます。

次の例では C2046 エラーが生成されます。

```
// C2046.cpp
int main() {
   case 0:   // C2046
}
```

考えられる解決方法:

```
// C2046b.cpp
int main() {
   int i = 0;

   switch(i) {
      case 0:
      break;

      default:
      break;
   }
}
```