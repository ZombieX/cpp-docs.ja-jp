---
title: CMFCTabToolTipInfo 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21e612615110370922d71e1acaebcda56b2e692e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435455"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo 構造体

この構造体は、ユーザーが配置されている MDI タブの情報を提供します。

## <a name="syntax"></a>構文

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>メンバー

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|タブ コントロールのインデックスを指定します。|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|タブ コントロールへのポインター。|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|ツールヒントのテキスト。|

## <a name="remarks"></a>Remarks

ポインターを`CMFCTabToolTipInfo`AFX_WM_ON_GET_TAB_TOOLTIP メッセージのパラメーターとして構造体が渡されます。 MDI タブが有効になっているし、ユーザーがタブ コントロールを置いたときに、このメッセージが生成されます。

## <a name="example"></a>例

次の例はどのように`CMFCTabToolTipInfo`で使用されて、 [MDITabsDemo サンプル: MFC タブ付き MDI アプリケーション](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

タブ コントロールのインデックスを指定します。

```
int m_nTabIndex;
```

### <a name="remarks"></a>Remarks

どのユーザーがポインターを合わせると、タブのインデックス。

### <a name="example"></a>例

次の例はどのように`m_nTabIndex`で使用されて、 [MDITabsDemo サンプル: MFC タブ付き MDI アプリケーション](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

タブ コントロールへのポインター。

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>例

次の例はどのように`m_pTabWnd`で使用されて、 [MDITabsDemo サンプル: MFC タブ付き MDI アプリケーション](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

ツールヒントのテキスト。

```
CString m_strText;
```

### <a name="remarks"></a>Remarks

文字列が空の場合、ツールヒントは表示されません。

### <a name="example"></a>例

次の例はどのように`m_strText`で使用されて、 [MDITabsDemo サンプル: MFC タブ付き MDI アプリケーション](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
