---
title: コンパイラの警告 (レベル 1) C4142 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 011f71c1d57f03c2be9bac3df67cd0ed90aa8017
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117388"
---
# <a name="compiler-warning-level-1-c4142"></a>コンパイラの警告 (レベル 1) C4142

問題のない型の再定義しています

型は、生成されたコードに影響が方法で再定義しません。

次のような原因をチェックして問題を解決するには:

- 派生クラスのメンバー関数は、基底クラスのメンバー関数は、対応するからさまざまな戻り値の型。

- 定義されている型、`typedef`別の構文を使用して、コマンドが再定義します。

次の例では、C4142 が生成されます。

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```