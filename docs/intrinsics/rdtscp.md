﻿---
title: _ _rdtscp |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65c4638112d87b0544e9a6c61d839c7ad4664d33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415162"
---
# <a name="rdtscp"></a>__rdtscp

**Microsoft 固有の仕様**

 `rdtscp`命令を生成してメモリに`TSC_AUX[31:0]`を書き込み、64 ビットのタイム スタンプ カウンター`(TSC)`を返します。

## <a name="syntax"></a>構文

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>パラメーター

*Aux*<br/>
[out]マシン固有のレジスタの内容を格納する場所へのポインター`TSC_AUX[31:0]`します。

## <a name="return-value"></a>戻り値

64 ビット符号なし整数のティック数。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__rdtscp`|AMD NPT ファミリ 0 fh または以降のバージョン|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>コメント

この組み込み関数は`rdtscp`命令を生成します。 この命令のハードウェア サポートを確認するには、組み込み関数`__cpuid`を`InfoType=0x80000001`として呼び出し、`CPUInfo[3] (EDX)`の 27 ビット目を確認してください。 命令がサポートされていればこのビットは 1 となり、サポートされていなければ 0 となります。  `rdtscp`命令が搭載されていないハードウェア上でこの組み込み関数を呼び出した場合、その結果は保証されません。

> [!CAUTION]
>  `rdtsc`とは異なり、`rdtscp`はシリアル化する命令です。ただし、コンパイラはこの組み込み命令を移動することがあります。  


この世代のハードウェアで TSC 値の解釈は、x64 の以前のバージョンとは異なります。  詳細についてはハードウェアのマニュアルを参照してください。

値`TSC_AUX[31:0]`の意味はオペレーティング システムによって異なります。

## <a name="example"></a>例

```
#include <intrin.h>
#include <stdio.h>
int main()
{
unsigned __int64 i;
unsigned int ui;
i = __rdtscp(&ui);
printf_s("%I64d ticks\n", i);
printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**Microsoft 固有の仕様はここまで**

高度なマイクロ デバイス, inc. copyright 2007All rights reserved. 高度なマイクロ デバイス, Inc. からのアクセス許可を持つ再現

## <a name="see-also"></a>関連項目

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
