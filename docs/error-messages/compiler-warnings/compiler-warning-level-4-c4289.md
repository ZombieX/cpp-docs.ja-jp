---
title: コンパイラの警告 (レベル 4) C4289 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4289
dev_langs:
- C++
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35cb22c767c0ea64a1536bd4d02ad8653bb94250
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102841"
---
# <a name="compiler-warning-level-4-c4289"></a>コンパイラの警告 (レベル 4) C4289

非標準の拡張が使用されています : 'var' : for ループで宣言したループ コントロール変数が for ループ スコープの外側で使用されています。

コンパイルするときに[/Ze](../../build/reference/za-ze-disable-language-extensions.md)と **/Zc:forScope-** で宣言された変数を[の](../../cpp/for-statement-cpp.md)後ループが使用された、**の**-スコープをループします。

参照してください[/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)で標準の動作を指定する方法については**の**ループの **/Ze**します。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4289 が生成されます。

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```