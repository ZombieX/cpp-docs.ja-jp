---
title: コンパイラ エラー C2012 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2012
dev_langs:
- C++
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 695576afc4daa7bff93d40ff1477dbc1a3b06363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111694"
---
# <a name="compiler-error-c2012"></a>コンパイラ エラー C2012

'<' の後にファイル名がありません。

`#include` ディレクティブに必要なファイル名がありません。

次の例では C2012 エラーが生成されます。

```
// C2012.cpp
#include <   // C2012 include the filename to resolve
```

考えられる解決方法:

```
// C2012b.cpp
// compile with: /c
#include <stdio.h>
```