---
title: Platform::invalidargumentexception クラス |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::InvalidArgumentException
- VCCORLIB/Platform::InvalidArgumentException::InvalidArgumentException
dev_langs:
- C++
helpviewer_keywords:
- Platform::InvalidArgumentException
ms.assetid: 1a8d860b-3bcb-41a9-9346-6610616a0b46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ccd6a2ac0b47db7d808f3f90a228ecf497e95be
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101861"
---
# <a name="platforminvalidargumentexception-class"></a>Platform::InvalidArgumentException クラス

メソッドに渡された引数のいずれかが無効な場合にスローされます。

## <a name="syntax"></a>構文

```cpp
public ref class InvalidArgumentException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Remarks

詳細については、 [COMException](../cppcx/platform-comexception-class.md) クラスを参照してください。

### <a name="requirements"></a>要件

**クライアントがサポートされている最小:** Windows 8

**サポートされているサーバーの最小値:** Windows Server 2012

**名前空間:** Platform

**メタデータ:** platform.winmd

## <a name="see-also"></a>関連項目

[Platform::COMException クラス](../cppcx/platform-comexception-class.md)