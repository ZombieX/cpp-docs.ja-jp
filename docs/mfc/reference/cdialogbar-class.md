---
title: CDialogBar クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dad3f7309d36f7233d871ea47a859c4e572140f6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065461"
---
# <a name="cdialogbar-class"></a>CDialogBar クラス

コントロール バー内の Windows のモードレス ダイアログ ボックスの機能を提供します。

## <a name="syntax"></a>構文

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|`CDialogBar` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDialogBar::Create](#create)|Windows ダイアログ バーを作成し、それにアタッチします、`CDialogBar`オブジェクト。|

## <a name="remarks"></a>Remarks

ダイアログ バーではその間、ユーザーのタブは標準の Windows コントロールが含まれているダイアログ ボックスに似ています。 他類似性は、ダイアログ バーを表すためのダイアログ テンプレートを作成することです。

作成して、ダイアログ バーを使用して、作成と使用のような`CFormView`オブジェクト。 まず、使用して、[ダイアログ エディター](../../windows/dialog-editor.md) WS_CHILD スタイルでダイアログ テンプレートとしないその他のスタイルを定義します。 テンプレートはスタイル WS_VISIBLE に必要ありません。 アプリケーション コードで構築するコンス トラクターを呼び出す、`CDialogBar`オブジェクト`Create`ダイアログ バーのウィンドウを作成し、アタッチ先、`CDialogBar`オブジェクト。

詳細については`CDialogBar`、記事をご覧ください[ダイアログ バー](../../mfc/dialog-bars.md)と[テクニカル ノート 31](../../mfc/tn031-control-bars.md)、コントロール バーです。

> [!NOTE]
>  現在のリリースで、`CDialogBar`オブジェクトは、Windows フォーム コントロールをホストできません。 Visual C での Windows フォーム コントロールの詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar

`CDialogBar` オブジェクトを構築します。

```
CDialogBar();
```

##  <a name="create"></a>  CDialogBar::Create

指定したダイアログ ボックス リソース テンプレートを読み込みます`lpszTemplateName`または`nIDTemplate`、ダイアログ バーのウィンドウを作成してスタイルを設定およびに関連付けます、`CDialogBar`オブジェクト。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
親へのポインター`CWnd`オブジェクト。

*lpszTemplateName*<br/>
名前へのポインター、`CDialogBar`オブジェクトのダイアログ ボックス リソース テンプレート。

*nStyle*<br/>
ツールバーのスタイル。 追加のスタイルは次のとおりです。

- CBRS_TOP コントロール バーは、フレーム ウィンドウの上部にあること。

- CBRS_BOTTOM コントロール バーでは、フレーム ウィンドウの下部にあります。

- 親のサイズが変更されたときに CBRS_NOALIGN コントロール バーの位置を変更できません。

- CBRS_TOOLTIPS コントロール バーには、ツール ヒントが表示されます。

- CBRS_SIZE_DYNAMIC コントロール バーは動的です。

- CBRS_SIZE_FIXED コントロール バーは固定されています。

- CBRS_FLOATING コントロール バーがフローティングします。

- CBRS_FLYBY ステータス バーには、ボタンに関する情報が表示されます。

- CBRS_HIDE_INPLACE コントロール バーがユーザーに表示されません。

*nID*<br/>
ダイアログ バーのコントロール ID。

*nIDTemplate*<br/>
リソース ID、`CDialogBar`オブジェクトのダイアログ ボックスのテンプレート。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

CBRS_TOP または CBRS_BOTTOM 配置スタイルを指定する場合は、ダイアログ バーの幅は、フレーム ウィンドウの高さは、によって指定されるリソースの*nIDTemplate*します。 CBRS_LEFT または CBRS_RIGHT 配置スタイルを指定する場合は、ダイアログ バーの高さは、フレーム ウィンドウの幅は、によって指定されるリソースの*nIDTemplate*します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプル CTRLBARS](../../visual-cpp-samples.md)<br/>
[CControlBar クラス](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFormView クラス](../../mfc/reference/cformview-class.md)<br/>
[CControlBar クラス](../../mfc/reference/ccontrolbar-class.md)
