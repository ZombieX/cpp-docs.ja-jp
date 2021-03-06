---
title: コンパイラの警告 (レベル 4) C4457 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62232a814bed47f8b6a5041d20e6f37776abffe8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093533"
---
# <a name="compiler-warning-level-4-c4457"></a>コンパイラの警告 (レベル 4) C4457

> 宣言 '*識別子*' 関数のパラメーターを非表示にします

宣言*識別子*ローカル スコープで同じ名前の関数パラメーターの宣言を非表示にします。 この警告を参照するかを把握できます。*識別子*ローカル スコープでないパラメーター、可能性のあるユーザーの意図ができない可能性があります、ローカルに宣言されたバージョンに解決します。 この問題を解決するには、パラメーター名と競合しないローカル変数名の提供をお勧めします。

## <a name="example"></a>例

次の例では、ため、C4457 が生成されますパラメーター`x`し、ローカル変数`x`で`member_fn`と同じ名前です。 この問題を解決するには、異なる名前をパラメーターとローカル変数を使用します。

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
