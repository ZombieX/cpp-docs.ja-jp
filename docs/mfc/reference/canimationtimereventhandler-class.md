---
title: CAnimationTimerEventHandler クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad48c372043c06c2bc3a64537734a30d79e81a50
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395001"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler クラス

タイミング イベントの発生時に Animation API によって呼び出されるコールバックを実装します。

## <a name="syntax"></a>構文

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|インスタンスを作成します`CAnimationTimerEventHandler`コールバック。|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|アニメーションの更新が完了した後に発生するイベントを処理します。 (`CUIAnimationTimerEventHandlerBase::OnPostUpdate` をオーバーライドします)。|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|アニメーションの更新プログラムを開始する前に発生するイベントを処理します。 (`CUIAnimationTimerEventHandlerBase::OnPreUpdate` をオーバーライドします)。|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|アニメーションのレンダリング フレーム レートが最小の望ましいフレーム レートを下回ったときに発生するイベントを処理します。 (`CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow` をオーバーライドします)。|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|イベントをルーティングするアニメーション コント ローラーへのポインターを格納します。|

## <a name="remarks"></a>Remarks

このイベント ハンドラーが作成され、CAnimationController::EnableAnimationTimerEventHandler を呼び出すときに、IUIAnimationTimer::SetTimerEventHandler に渡されます。

## <a name="inheritance-hierarchy"></a>継承階層

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>要件

**ヘッダー:** afxanimationcontroller.h

##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance

CAnimationTimerEventHandler コールバックのインスタンスを作成します。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>パラメーター

*pAnimationController*<br/>
イベントを受信するアニメーション コント ローラーへのポインター。

*ppTimerEventHandler*

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate

アニメーションの更新が完了した後に発生するイベントを処理します。

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は s_ok を返します。それ以外の場合 E_FAIL します。

##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate

アニメーションの更新プログラムを開始する前に発生するイベントを処理します。

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は s_ok を返します。それ以外の場合 E_FAIL します。

##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow

アニメーションのレンダリング フレーム レートが最小の望ましいフレーム レートを下回ったときに発生するイベントを処理します。

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>パラメーター

*fps*

### <a name="return-value"></a>戻り値

メソッドが成功した場合は s_ok を返します。それ以外の場合 E_FAIL します。

##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController

イベントをルーティングするアニメーション コント ローラーへのポインターを格納します。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>パラメーター

*pAnimationController*<br/>
イベントを受信するアニメーション コント ローラーへのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
