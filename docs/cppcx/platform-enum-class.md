---
title: Platform::enum クラス |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Enum
dev_langs:
- C++
helpviewer_keywords:
- Platform::Enum Struct
ms.assetid: cf82f0eb-7a37-4e4e-bbe7-e4aebbc9ec0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0568fba448d6f6976df466c46569e5059fb11ddf
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105227"
---
# <a name="platformenum-class"></a>Platform::Enum クラス

一連の名前付き定数を表す値クラス。

## <a name="syntax"></a>構文

```cpp
public class Enum
```

### <a name="members"></a>メンバー

Enum クラスは、 [Platform::Object Class](../cppcx/platform-object-class.md)の Equals()、GetHashCode()、および ToString() の各メソッドを継承します。

### <a name="remarks"></a>Remarks

列挙型を作成するには、 [パブリック列挙型クラス](../windows/enum-class-cpp-component-extensions.md) キーワードを使用します。 Platform::Enum 型は明示的に使用しないでください。 詳細については、「 [列挙体](../cppcx/enums-c-cx.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。

### <a name="requirements"></a>要件

**クライアントがサポートされている最小:** Windows 8

**サポートされているサーバーの最小値:** Windows Server 2012

**名前空間:** Platform

**メタデータ:** platform.winmd

## <a name="see-also"></a>関連項目

[Platform 名前空間](../cppcx/platform-namespace-c-cx.md)