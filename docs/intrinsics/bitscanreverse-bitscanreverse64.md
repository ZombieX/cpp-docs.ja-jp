---
title: _BitScanReverse、_BitScanReverse64 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
dev_langs:
- C++
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0867241e983794177cdb53b4bbacd1aadd9b8eba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436326"
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse、_BitScanReverse64

**Microsoft 固有の仕様**

マスク データの最上位ビット (MSB) から最下位ビット (LSB) に向かって設定済みビット (1) を検索します。

## <a name="syntax"></a>構文

```
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

#### <a name="parameters"></a>パラメーター

*Index*<br/>
[out]見つかった最初のビット セット (1) のビット位置が読み込まれます。

*マスク*<br/>
[in]検索する 32 ビットまたは 64 ビット値。

## <a name="return-value"></a>戻り値

`Index` が設定された場合は 0 以外、設定済みビットが見つからなかった場合は 0。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_BitScanReverse`|x86、ARM、x64|\<intrin.h>|
|`_BitScanReverse64`|ARM、x64||

## <a name="example"></a>例

```
// BitScanReverse.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanReverse)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanReverse(&index, mask);
   if (isNonzero)
   {
      cout << "Mask: " << mask << " Index: " << index << endl;
   }
   else
   {
      cout << "No set bits found.  Mask is zero." << endl;
   }
}
```

## <a name="input"></a>入力

```
12
```

## <a name="sample-output"></a>出力例

```
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)