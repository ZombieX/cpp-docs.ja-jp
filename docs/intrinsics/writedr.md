---
title: _ _writedr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fd9bd5145947711c245f552672843d604160d06
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402175"
---
# <a name="writedr"></a>__writedr

指定されたデバッグ登録するには、指定した値を書き込みます。

## <a name="syntax"></a>構文

```
void __writedr(unsigned DebugRegister, unsigned DebugValue);
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);
```

#### <a name="parameters"></a>パラメーター

*DebugRegister*<br/>
[in]デバッグを識別する 0 ~ 7 の数値を登録します。

*DebugValue*<br/>
[in]デバッグ用に記述する値を登録します。

## <a name="remarks"></a>Remarks

これらの組み込みはカーネル モードでのみ使用できますし、ルーチンは組み込みとしてのみ使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writedr`|x86、x64|

**ヘッダー ファイル** \<intrin.h >

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)<br/>
[__readdr](../intrinsics/readdr.md)