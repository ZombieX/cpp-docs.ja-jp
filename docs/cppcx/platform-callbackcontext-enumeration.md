---
title: Platform::callbackcontext 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe988a7dee7fb358d9454c06811d7baf2cd4ace0
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101964"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 列挙型

コールバック関数 (イベント ハンドラー) が実行するスレッド コンテキストを指定します。

## <a name="syntax"></a>構文

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>メンバー

|型コード|説明|
|---------------|-----------------|
|どれでも可|コールバック関数は、任意のスレッド コンテキストで実行できます。|
|同|コールバック関数は、非同期操作を開始したスレッド コンテキストでのみ実行できます。|

### <a name="requirements"></a>要件

**クライアントがサポートされている最小:** Windows 8

**サポートされているサーバーの最小値:** Windows Server 2012

**名前空間:** Platform

**メタデータ:** platform.winmd