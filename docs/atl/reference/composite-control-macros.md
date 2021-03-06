---
title: 複合コントロールに関するマクロ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75e34fd4cfa53257f0e8a497cf8bc245c90f6732
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077355"
---
# <a name="composite-control-macros"></a>複合コントロールに関するマクロ

これらのマクロは、イベント シンク マップとエントリを定義します。

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|複合コントロールのイベント シンク マップの先頭をマークします。|
|[END_SINK_MAP](#end_sink_map)|複合コントロールのイベント シンク マップの終了を示します。|
|[SINK_ENTRY](#sink_entry)|イベント シンク マップするエントリ。|
|[SINK_ENTRY_EX](#sink_entry_ex)|追加のパラメーターでイベント シンク マップするエントリ。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017)Iid へのポインターを受け取る点を除いて、SINK_ENTRY_EX 類似します。|
|[SINK_ENTRY_INFO](#sink_entry_info)|使用するための手動で指定された型情報とイベント シンク マップするエントリ[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)します。|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017)Iid へのポインターを受け取る点を除いて、SINK_ENTRY_INFO 類似します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="begin_sink_map"></a>  BEGIN_SINK_MAP

複合コントロールのイベント シンク マップの先頭を宣言します。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>パラメーター

*(_c)*<br/>
[in]コントロールを指定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Remarks

ActiveX イベント シンクのみサポートの戻り値の HRESULT 型または void、イベント ハンドラー メソッドからの CE ATL の実装その他の戻り値はサポートされていませんし、その動作は未定義です。

##  <a name="end_sink_map"></a>  END_SINK_MAP

複合コントロールのイベント シンク マップの末尾を宣言します。

```
END_SINK_MAP()
```

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Remarks

ActiveX イベント シンクのみサポートの戻り値の HRESULT 型または void、イベント ハンドラー メソッドからの CE ATL の実装その他の戻り値はサポートされていませんし、その動作は未定義です。

##  <a name="sink_entry"></a>  SINK_ENTRY

ハンドラー関数を宣言します (*fn*) 指定したイベント (*dispid*) で指定されたコントロールの*id*します。

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]コントロールを識別します。

*dispid*<br/>
[in]指定したイベントを識別します。

*fn*<br/>
[in]イベント ハンドラー関数の名前です。 この関数を使用する必要があります、`_stdcall`呼び出し規約と dispinterface スタイルの適切な署名があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Remarks

ActiveX イベント シンクのみサポートの戻り値の HRESULT 型または void、イベント ハンドラー メソッドからの CE ATL の実装その他の戻り値はサポートされていませんし、その動作は未定義です。

##  <a name="sink_entry_ex"></a>  SINK_ENTRY_EX と SINK_ENTRY_EX_P

ハンドラー関数を宣言します (*fn*) 指定したイベント (*dispid*)、ディスパッチ インターフェイスの (*iid*) で指定されたコントロールの*id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]コントロールを識別します。

*iid*<br/>
[in]ディスパッチ インターフェイスを識別します。

*piid*<br/>
[in]ディスパッチ インターフェイスへのポインター。

*dispid*<br/>
[in]指定したイベントを識別します。

*fn*<br/>
[in]イベント ハンドラー関数の名前です。 この関数を使用する必要があります、`_stdcall`呼び出し規約と dispinterface スタイルの適切な署名があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Remarks

ActiveX イベント シンクのみサポートの戻り値の HRESULT 型または void、イベント ハンドラー メソッドからの CE ATL の実装その他の戻り値はサポートされていませんし、その動作は未定義です。

##  <a name="sink_entry_info"></a>  SINK_ENTRY_INFO と SINK_ENTRY_INFO_P

必要な情報を提供するイベント シンク マップ内を使用して[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)関連するハンドラー関数にイベントをルーティングします。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]イベント ソースを識別する符号なし整数。 この値に一致する必要があります、 *nID*関連で使用するテンプレート パラメーター [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)基本クラス。

*iid*<br/>
[in]ディスパッチ インターフェイスを識別する IID。

*piid*<br/>
[in]ディスパッチ インターフェイスを識別する IID へのポインター。

*dispid*<br/>
[in]指定したイベントを識別するように DISPID。

*fn*<br/>
[in]イベント ハンドラー関数の名前です。 この関数を使用する必要があります、`_stdcall`呼び出し規約と dispinterface スタイルの適切な署名があります。

*情報*<br/>
[in]イベント ハンドラー関数の情報を入力します。 この型情報がへのポインターの形で提供される、`_ATL_FUNC_INFO`構造体。 CC_CDECL の CALLCONV フィールド for Windows CE でサポートされる唯一のオプション、`_ATL_FUNC_INFO`構造体。 その他の値はサポートされていませんので、動作が定義されていません。

### <a name="remarks"></a>Remarks

最初の 4 つのマクロのパラメーターは、のものと同じ、 [SINK_ENTRY_EX](#sink_entry_ex)マクロ。 最後のパラメーターは、イベントの種類の情報を提供します。 ActiveX イベント シンクのみサポートの戻り値の HRESULT 型または void、イベント ハンドラー メソッドからの CE ATL の実装その他の戻り値はサポートされていませんし、その動作は未定義です。

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)<br/>
[複合コントロールに関するグローバル関数](../../atl/reference/composite-control-global-functions.md)
