---
title: コンパイラの警告 (レベル 1) C4807 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8eecbd1e7c9c88ec463224b9738cebbf9ff8f4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039869"
---
# <a name="compiler-warning-level-1-c4807"></a>コンパイラの警告 (レベル 1) C4807

'operation': 'type' 型と 'type' 型の符号付きビットフィールドの混用は安全ではありません。

この警告は、1 ビットの符号付きビットフィールドと `bool` 変数を比較すると、生成されます。 1 ビットの符号付きビットフィールドには、値 -1 または 0 のみを含めることがでるため、 `bool`と比較するのは危険です。 `bool` と 1 ビットの符号なしビットフィールドは `bool` を同じであり、0 または 1 のみを保持できるため、これらを混用しても警告は生成されません。

## <a name="example"></a>例

次の例では C4807 が生成されます。

```
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```