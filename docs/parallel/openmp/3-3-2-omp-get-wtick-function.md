---
title: 3.3.2 omp_get_wtick 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0111e7ee1d4eba0a7ca9edf50d99cef8d052f6a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380315"
---
# <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 関数

`omp_get_wtick`連続クロックのティック間関数が秒数に等しいにある倍精度浮動小数点値を返します。 形式は次のとおりです。

```
#include <omp.h>
double omp_get_wtick(void);
```