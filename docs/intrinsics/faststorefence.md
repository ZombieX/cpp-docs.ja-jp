---
title: _ _faststorefence の |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __faststorefence_cpp
- __faststorefence
dev_langs:
- C++
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5047dbb2023272ab03cc7d49f877f0fcc38a7b76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402188"
---
# <a name="faststorefence"></a>__faststorefence

**Microsoft 固有の仕様**

メモリ参照の読み込みと格納の両方を含む、以前の各メモリ参照が、後続のメモリ参照の前に全体に対して参照可能になっていることを保証します。

## <a name="syntax"></a>構文

```
void __faststorefence();
```

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__faststorefence`|X64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

この組み込みの前に発生した読み込みおよび格納操作が、実行が続行する前に全体に対して参照可能になっていることを保証する、完全なメモリ バリアの命令シーケンスを生成します。 効果は、すべての x64 プラットフォームにおける `_mm_mfence` の組み込みと同等ですが、それよりも高速になります。

AMD64 プラットフォームでは、このルーチンは、`sfence` 命令よりも高速なストア フェンスである命令を生成します。 タイム クリティカル コードでは、`_mm_sfence` ではなくこの組み込みを使用します (AMD64 プラットフォームのみ)。 Intel x64 プラットフォームでは、 `_mm_sfence` 命令は高速化します。

このルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)