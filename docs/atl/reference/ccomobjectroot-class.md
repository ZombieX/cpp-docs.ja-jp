---
title: CComObjectRoot クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2647ea3ac46ec3783f584de996c3d988c168980d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054864"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot クラス

この typedef の[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)スレッド モデルがサーバーの既定のテンプレート化されます。

## <a name="syntax"></a>構文

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Remarks

`CComObjectRoot` `typedef`の[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)スレッド モデルがサーバーの既定のテンプレート化します。 したがって[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)いずれかを参照[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)または[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)します。

`CComObjectRootEx` 非集計と集計の両方のオブジェクトのオブジェクト参照カウントの管理を処理します。 オブジェクトが集計されていませんし、オブジェクトが集約されている場合、不明な外部へのポインターを保持する場合は、オブジェクトの参照カウントを保持します。 集計のオブジェクトの`CComObjectRootEx`を構築する内部オブジェクトのエラーを処理するメソッドを使用でき、内部のインターフェイスがリリースされたときに削除されないように、外側のオブジェクトまたは内部のオブジェクトを保護するために削除されます。

## <a name="requirements"></a>要件

**ヘッダー:** atlcom.h

## <a name="see-also"></a>関連項目

[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject クラス](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject クラス](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject クラス](../../atl/reference/ccompolyobject-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
