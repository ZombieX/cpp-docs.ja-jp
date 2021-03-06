---
title: コンパイラ エラー C3873 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83580d8202dada0b650b1703dcadf9b99e6771d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072811"
---
# <a name="compiler-error-c3873"></a>コンパイラ エラー C3873

'char': この文字を識別子の最初の文字にすることはできません

C++ コンパイラは、識別子で許可される文字に関する C++11 標準に従います。 識別子では、特定の範囲の文字とユニバーサル文字名しか使用できません。 識別子の最初の文字に追加の制限が適用されます。 許可される文字の一覧とユニバーサル文字名の範囲については、「 [Identifiers](../../cpp/identifiers-cpp.md)」を参照してください。

識別子で許可される文字の範囲は、C++/CLI コードをコンパイルする場合よりも制限されません。 /clr を使用してコンパイルするコード内の識別子は、  [標準 ECMA 335: 共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)に従う必要があります。

次の例では警告 C3873 が生成されます。

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```