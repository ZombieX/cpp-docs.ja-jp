---
title: コンパイラの警告 (レベル 4) C4725 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4725
dev_langs:
- C++
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef56a4e580e8c62db7f8c8c818a84acec0214672
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048267"
---
# <a name="compiler-warning-level-4-c4725"></a>コンパイラの警告 (レベル 4) C4725

Pentium のモデルによっては、命令が不正確になります。

コードにインライン アセンブリ命令が含まれていますが、これは Pentium マイクロプロセッサのモデルによっては正確な結果が得られないことがあります。

次の例では C4725 が生成されます。

```
// C4725.cpp
// compile with: /W4
// processor: x86
double m32fp = 2.0003e-17;

void f() {
   __asm
   {
      FDIV m32fp   // C4725
   }
}

int main() {
}
```