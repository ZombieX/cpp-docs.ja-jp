---
title: コンパイラの警告 C4439 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 646b057f3f25bec8b686b08d50f0e473542ddcfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076113"
---
# <a name="compiler-warning-c4439"></a>コンパイラの警告 C4439

'function': シグネチャのマネージ型と関数定義は、_ _clrcall 呼び出し規約をいる必要があります

コンパイラの呼び出し規約を暗黙的に置き換えられます[_ _clrcall](../../cpp/clrcall.md)します。 この警告を解決するには、削除、`__cdecl`または`__stdcall`呼び出し規約。

C4439 は常に、エラーとして発行されます。 この警告をオフにすることができます、`#pragma warning`または **/wd**; を参照してください[警告](../../preprocessor/warning.md)または[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、//we、/wo、/Wv、/WX (警告レベル)](../../build/reference/compiler-option-warning-level.md)詳細についてはします。

## <a name="example"></a>例

次の例では、C4439 が生成されます。

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```