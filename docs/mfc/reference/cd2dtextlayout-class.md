---
title: CD2DTextLayout クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a699744955088ad49c0e701166cf368695354fac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402201"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout クラス

IDWriteTextLayout のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|CD2DTextLayout オブジェクトを構築します。|
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|デストラクターです。 D2D テキスト レイアウト オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|CD2DTextLayout を作成します。 (上書き[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create))。|
|[CD2DTextLayout::Destroy](#destroy)|CD2DTextLayout オブジェクトを破棄します。 (上書き[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy))。|
|[CD2DTextLayout::Get](#get)|返します IDWriteTextLayout インターフェイス|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|指定した位置にあるテキストのフォント ファミリ名をコピーします。|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|指定した位置にあるテキストのロケール名を取得します。|
|[CD2DTextLayout::IsValid](#isvalid)|リソースの有効性を確認します (上書き[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid))。|
|[CD2DTextLayout::ReCreate](#recreate)|CD2DTextLayout を再作成します。 (上書き[CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate))。|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|指定したテキスト範囲内のテキスト セットの null で終わるフォント ファミリ名|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|指定したテキスト範囲内のテキストのロケール名を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|返します IDWriteTextLayout インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|IDWriteTextLayout へのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout:: ~ CD2DTextLayout

デストラクターです。 D2D テキスト レイアウト オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DTextLayout();
```

##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout

CD2DTextLayout オブジェクトを構築します。

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*strText*<br/>
新しい CD2DTextLayout オブジェクトを作成する文字列を含む CString オブジェクト。

*TextFormat*<br/>
文字列に適用する書式を含む CString オブジェクトを指定します。

*sizeMax*<br/>
[レイアウト] ボックスのサイズ。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DTextLayout::Create

CD2DTextLayout を作成します。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DTextLayout::Destroy

CD2DTextLayout オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextLayout::Get

返します IDWriteTextLayout インターフェイス

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>戻り値

IDWriteTextLayout インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName

指定した位置にあるテキストのフォント ファミリ名をコピーします。

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>パラメーター

*currentPosition*<br/>
確認するテキストの位置。

*TextRange*<br/>
同じテキストの範囲は、currentPosition で指定された位置にあるテキストとして書式設定します。 つまり、実行には、フォント ファミリ名など、指定された位置として、正確な書式設定します。

### <a name="return-value"></a>戻り値

現在のフォント ファミリ名を含む CString オブジェクト。

##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName

指定した位置にあるテキストのロケール名を取得します。

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>パラメーター

*currentPosition*<br/>
検査するテキストの位置。

*TextRange*<br/>
同じテキストの範囲は、currentPosition で指定された位置にあるテキストとして書式設定します。 つまり、実行には、ロケール名などの位置指定すると、正確な書式設定します。

### <a name="return-value"></a>戻り値

現在のロケール名を含む CString オブジェクト。

##  <a name="isvalid"></a>  CD2DTextLayout::IsValid

リソースの有効性のチェック

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout

IDWriteTextLayout へのポインター。

```
IDWriteTextLayout* m_pTextLayout;
```

##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout *

返します IDWriteTextLayout インターフェイス

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>戻り値

IDWriteTextLayout インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="recreate"></a>  CD2DTextLayout::ReCreate

CD2DTextLayout を再作成します。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName

指定したテキスト範囲内のテキスト セットの null で終わるフォント ファミリ名

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>パラメーター

*pwzFontFamilyName*<br/>
TextRange で指定された範囲内で文字列全体に適用されるフォント ファミリ名

*TextRange*<br/>
この変更を適用するテキスト範囲

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE が返されます

##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName

指定したテキスト範囲内のテキストのロケール名を設定します。

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>パラメーター

*pwzLocaleName*<br/>
Null で終わるロケール名の文字列

*TextRange*<br/>
この変更を適用するテキスト範囲

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE が返されます

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
