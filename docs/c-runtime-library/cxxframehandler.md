---
title: __CxxFrameHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4141d932cfad78ca9c563334ebbe51f711153e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088723"
---
# <a name="cxxframehandler"></a>__CxxFrameHandler

内部 CRT 関数。 構造化例外フレームを処理するために CRT によって使用されます。

## <a name="syntax"></a>構文

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>パラメーター

*pExcept*<br/>
使用可能な `catch` ステートメントに渡される例外レコード。

*pRN*<br/>
例外を処理するために使用されるスタック フレームに関する動的な情報。 詳細については、「ehdata.h」を参照してください。

*pContext*<br/>
コンテキスト。 (Intel プロセッサでは使用されません)。

*pDC*<br/>
関数の開始とスタック フレームに関する追加情報。

## <a name="return-value"></a>戻り値

[try-except ステートメント](../cpp/try-except-statement.md)によって使用される*フィルター式*の値のいずれか。

## <a name="remarks"></a>コメント

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h、ehdata.h|