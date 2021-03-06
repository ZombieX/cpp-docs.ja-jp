---
title: 2.6.2 critical コンストラクト |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e51bd425999081c7a06a7d5692dbea16c887fa0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417853"
---
# <a name="262-critical-construct"></a>2.6.2 critical コンストラクト

**重要な**ディレクティブは、一度に 1 つのスレッドに関連付けられている構造化ブロックの実行を制限する構成要素を識別します。 構文、**重要な**ディレクティブを次に示します。

```
#pragma omp critical [(name)]  new-linestructured-block
```

省略可能な*名前*クリティカル領域を識別するために使用可能性があります。 重要な領域を識別するために使用される識別子は外部リンケージを持ち、ラベル、タグ、メンバー、および通常の識別子で使用される名前空間とは別の名前空間には。

スレッドは、他のスレッドが同じ名前の重要な領域 (任意の場所でプログラム) を実行していないまで、クリティカル領域の先頭に待機します。 名前のないすべて**重要な**ディレクティブが指定されていない名前が同じものにマップします。