---
title: コンパイラの警告 (レベル 4) C4459 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4459
dev_langs:
- C++
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0fc86be746bafdf4987a7492c59d9686535cef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040896"
---
# <a name="compiler-warning-level-4-c4459"></a>コンパイラの警告 (レベル 4) C4459

> 宣言 '*識別子*' グローバル宣言を隠します

宣言*識別子*ローカル スコープで、同じ名前の宣言を非表示に*識別子*グローバル スコープでします。 この警告を参照するかを把握できます。*識別子*このスコープでの解決をローカルに宣言されたバージョンにグローバル バージョンではなく、可能性のあるユーザーの意図ができない可能性があります。 一般に、優れたエンジニア リング手法としてグローバル変数の使用を最小限に抑えることをお勧めします。 グローバル名前空間の汚染を最小化するには、グローバル変数の名前付きの名前空間の使用をお勧めします。

この警告は、Visual Studio 2015、Visual c コンパイラ バージョン 18.00 で新しく追加されました。 または、コードを移行する際に、後で、コンパイラのバージョンからの警告を抑制するのには、使用、 [/Wv:18](../../build/reference/compiler-option-warning-level.md)コンパイラ オプション。

## <a name="example"></a>例

次の例では、C4459 が生成されます。

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

この問題を解決する方法の 1 つが、グローバル変数の名前空間の作成が、使用するには、`using`ディレクティブのすべての参照を使用する必要があります、明確なので、スコープにその名前空間を含めるには修飾名。

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
