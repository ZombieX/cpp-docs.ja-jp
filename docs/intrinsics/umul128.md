---
title: _umul128 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __umul128
dev_langs:
- C++
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6ca4db1103494c8c55d792391ac714311a3a7cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444082"
---
# <a name="umul128"></a>_umul128

**Microsoft 固有の仕様**

最初の 2 つの引数で渡された 2 つの 64 ビット符号なし整数を乗算し、その積の上位 64 ビットを `HighProduct` の指す 64 ビットの符号なし整数に格納して、積の下位 64 ビットを返します。

## <a name="syntax"></a>構文

```
unsigned __int64 _umul128( 
   unsigned __int64 Multiplier, 
   unsigned __int64 Multiplicand, 
   unsigned __int64 *HighProduct 
);
```

#### <a name="parameters"></a>パラメーター

*乗数*<br/>
[in]乗算する最初の 64 ビット整数。

*Multiplicand*<br/>
[in]乗算する 2 つ目の 64 ビット整数。

*HighProduct*<br/>
[out]製品の上位 64 ビット。

## <a name="return-value"></a>戻り値

積の下位 64 ビット。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_umul128`|ARM、x64|\<intrin.h>|

## <a name="example"></a>例

```
// umul128.c
// processor: IPF, x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)