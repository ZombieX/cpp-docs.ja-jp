---
title: 致命的なエラー C1070 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1070
dev_langs:
- C++
helpviewer_keywords:
- C1070
ms.assetid: 1058269a-5db6-4c23-a97f-b5269eb9188b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7e871b69bb189140a4001d574736a255eefaf61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055625"
---
# <a name="fatal-error-c1070"></a>致命的なエラー C1070

ファイル 'filename' 中で #if と #endif が対応していません

`#if`、 `#ifdef`、 `#ifndef` のいずれかのディレクティブには、対応する `#endif`がありません。

次の例では C1070 が生成されます。

```
// C1070.cpp
#define TEST

#ifdef TEST

#ifdef TEST
#endif
// C1070
```

考えられる解決策:

```
// C1070b.cpp
// compile with: /c
#define TEST

#ifdef TEST
#endif

#ifdef TEST
#endif
```