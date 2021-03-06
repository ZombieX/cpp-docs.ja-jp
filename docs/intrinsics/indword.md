---
title: _ _indword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __indword_cpp
- __indword
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 554cccba1d45cf172645c46e00fdb20c19ea42d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389604"
---
# <a name="indword"></a>__indword

**Microsoft 固有の仕様**

使用して、指定されたポートからのデータの 1 つのダブル ワードを読み取り、`in`命令。

## <a name="syntax"></a>構文

```
unsigned long __indword(
   unsigned short Port
);
```

#### <a name="parameters"></a>パラメーター

*ポート*<br/>
[in]読み取るポート。

## <a name="return-value"></a>戻り値

単語は、ポートから読み取ります。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__indword`|x86、x64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

このルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)