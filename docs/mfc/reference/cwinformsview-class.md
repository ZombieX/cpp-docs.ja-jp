---
title: CWinFormsView クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4d90f2a7f964d264966d5254d051ebddaf2baa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448143"
---
# <a name="cwinformsview-class"></a>CWinFormsView クラス

Windows フォーム コントロールのホスティング用の汎用機能を MFC ビューとして提供します。

## <a name="syntax"></a>構文

```
class CWinFormsView : public CView;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|`CWinFormsView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Windows フォーム コントロールへのポインターを取得します。|

### <a name="public-operators"></a>パブリック演算子

|名前||
|----------|-|
|[CWinFormsView::operator コントロール ^](#operator_control)|Windows フォーム コントロールへのポインターとして型をキャストします。|

## <a name="remarks"></a>Remarks

MFC を使用して、 `CWinFormsView` MFC ビュー内での .NET Framework Windows フォーム コントロールをホストするクラス。 コントロールは、ネイティブ ビューの子であるし、MFC ビューの全体のクライアント領域を占有します。 結果は、`CFormView`ビューで、Windows フォーム デザイナーを利用し、実行時に豊富なフォーム ベースのビューを作成することができます。

Windows フォームの使用に関する詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

> [!NOTE]
>  MFC Windows フォームの統合は、MFC と動的にリンクするプロジェクトでのみ機能 (プロジェクトの AFXDLL が定義されている場合)。

> [!NOTE]
>  CWinFormsView は MFC スプリッター ウィンドウをサポートしていません ( [CSplitterWnd クラス](../../mfc/reference/csplitterwnd-class.md))。 現在のみ Windows フォームのスプリッター コントロールがサポートされています。

## <a name="requirements"></a>要件

**ヘッダー:** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

`CWinFormsView` オブジェクトを構築します。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>パラメーター

*pManagedViewType*<br/>
Windows フォーム ユーザー コントロールのデータ型へのポインター。

### <a name="example"></a>例

次の例では、`CUserView`クラスから継承`CWinFormsView`の型を渡すと`UserControl1`を`CWinFormsView`コンス トラクター。 `UserControl1` カスタム ビルド ControlLibrary1.dll コントロールです。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  CWinFormsView::GetControl

Windows フォーム コントロールへのポインターを取得します。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>戻り値

ポインターを`System.Windows.Forms.Control`オブジェクト。

### <a name="remarks"></a>Remarks

Windows フォームを使用する方法の例は、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

##  <a name="operator_control"></a>  CWinFormsView::operator コントロール ^

Windows フォーム コントロールへのポインターとして型をキャストします。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Remarks

この演算子は、渡すことができます、`CWinFormsView`型の Windows フォーム コントロールへのポインターを受け取る関数をビュー<xref:System.Windows.Forms.Control>します。

### <a name="example"></a>例

  参照してください[CWinFormsView::GetControl](#getcontrol)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl クラス](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog クラス](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView クラス](../../mfc/reference/cformview-class.md)
