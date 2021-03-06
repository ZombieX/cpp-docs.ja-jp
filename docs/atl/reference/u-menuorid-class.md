---
title: _U_MENUorID クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3eb9ab5f08fe1984e52ed16eb26064093fb8e003
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052955"
---
# <a name="umenuorid-class"></a>_U_MENUorID クラス

このクラスのラッパーを提供する`CreateWindow`と`CreateWindowEx`します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class _U_MENUorID
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|コンストラクターです。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|メニューへのハンドル。|

## <a name="remarks"></a>Remarks

この引数のアダプター クラスは、呼び出し元の側 (ついて) Id またはメニューのハンドルの明示的なキャストを必要とせず、関数に渡される (HMENUs) のいずれかを使用できます。

このクラスは、Windows API にラッパーを実装するために設計されていますが、特に[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)と[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)が子ウィンドウがあります HMENU 引数を受け取るいずれ関数。識別子 (UINT) ではなくメニュー ハンドル。 たとえば、このクラスの使用を表示のパラメーターとして[CWindowImpl::Create](cwindowimpl-class.md#create)します。

クラスは、2 つのコンス トラクター オーバー ロードを定義します。 UINT 引数を受け取るいずれかと、その他の HMENU 引数を受け取ります。 UINT 引数は、コンス トラクターとクラスの 1 つのデータのメンバーに格納されている結果の HMENU にキャスト[m_hMenu](#_u_menuorid__m_hmenu)します。 HMENU コンス トラクターの引数は、変換せずに直接格納されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu

クラスは、パブリックの HMENU データ メンバーとしてコンス トラクターのいずれかに渡される値を保持します。

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID

UINT 引数は、コンス トラクターとクラスの 1 つのデータのメンバーに格納されている結果の HMENU にキャスト[m_hMenu](#_u_menuorid__m_hmenu)します。

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
子ウィンドウの識別子。

*hMenu*<br/>
メニューのハンドル。

### <a name="remarks"></a>Remarks

HMENU コンス トラクターの引数は、変換せずに直接格納されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
