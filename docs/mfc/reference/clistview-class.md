---
title: CListView クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
dev_langs:
- C++
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fbb9561111a75011f934aeb0ce972829132cb87
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423404"
---
# <a name="clistview-class"></a>CListView クラス

リスト コントロールとの使用を簡略化[CListCtrl](../../mfc/reference/clistctrl-class.md)MFC のドキュメント/ビュー アーキテクチャのリスト コントロールの機能をカプセル化するクラス。

## <a name="syntax"></a>構文

```
class CListView : public CCtrlView
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CListView::CListView](#clistview)|`CListView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|ビューに関連付けられているリスト コントロールを返します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|リスト ビューから指定されたイメージのリストを削除します。|

## <a name="remarks"></a>Remarks

このアーキテクチャの詳細については、「の概要、 [CView](../../mfc/reference/cview-class.md)クラスとクロス リファレンスがあります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>要件

**ヘッダー:** afxcview.h

##  <a name="clistview"></a>  CListView::CListView

`CListView` オブジェクトを構築します。

```
CListView();
```

##  <a name="getlistctrl"></a>  CListView::GetListCtrl

ビューに関連付けられているリスト コントロールへの参照を取得するには、このメンバー関数を呼び出します。

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>戻り値

ビューに関連付けられているリスト コントロールへの参照。

### <a name="example"></a>例

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

##  <a name="removeimagelist"></a>  CListView::RemoveImageList

リスト ビューから指定されたイメージのリストを削除します。

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>パラメーター

*nImageList*<br/>
削除するイメージの 0 から始まるインデックス。

## <a name="see-also"></a>関連項目

[MFC サンプル rowlist で](../../visual-cpp-samples.md)<br/>
[CCtrlView クラス](../../mfc/reference/cctrlview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView クラス](../../mfc/reference/cctrlview-class.md)
