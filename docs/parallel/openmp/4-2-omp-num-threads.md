---
title: 4.2 OMP_NUM_THREADS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9996a09661d962eb5e936fdb484c9dd534e46904
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445192"
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

**OMP_NUM_THREADS**その数は、明示的に呼び出すことで変更しない限り、環境変数は、実行中に使用するスレッドの既定の数を設定、 **omp_set_num_threads**ライブラリ ルーチンまたは明示的な**num_threads**句、**並列**ディレクティブ。

値、 **OMP_NUM_THREADS**環境変数は、正の整数である必要があります。 その効果は、スレッドの数を動的に調整が有効になっているかどうかによって異なります。 包括的な一連のルール間の相互作用についての**OMP_NUM_THREADS**環境、スレッドの変数および動的な調整は、8 ページの 2.3 のセクションを参照してください。

値が指定されていない場合、 **OMP_NUM_THREADS**環境変数、または指定された値が正の整数ではありませんか、値がスレッドの最大数よりも大きい場合、システムができるサポート、使用するスレッドの数実装定義です。

例:

```
setenv OMP_NUM_THREADS 16
```

## <a name="cross-references"></a>クロス リファレンス

- **num_threads**句を参照してください[セクション 2.3](../../parallel/openmp/2-3-parallel-construct.md) 8 ページの。

- **omp_set_num_threads**関数を参照してください[セクション 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 ページ。

- **omp_set_dynamic**関数を参照してください[セクション 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 ページ。