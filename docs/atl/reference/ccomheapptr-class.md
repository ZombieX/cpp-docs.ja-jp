---
title: CComHeapPtr クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3455e88c5a9852c902702544a0f915e8d20dc64e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043236"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr クラス

ヒープのポインターを管理するためのスマート ポインター クラス。

## <a name="syntax"></a>構文

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ヒープに格納されるオブジェクトの種類。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|コンストラクターです。|

## <a name="remarks"></a>Remarks

`CComHeapPtr` 派生した`CHeapPtr`が使用して[CComAllocator](../../atl/reference/ccomallocator-class.md) COM ルーチンを使用してメモリを割り当てることです。 参照してください[CHeapPtr](../../atl/reference/cheapptr-class.md)と[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)の使用可能なメソッドです。

## <a name="inheritance-hierarchy"></a>継承階層

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>要件

**ヘッダー:** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

コンストラクターです。

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>パラメーター

*pData*<br/>
既存の `CComHeapPtr` オブジェクト。

### <a name="remarks"></a>Remarks

既存を使用して、ヒープのポインターを作成することができます必要に応じて`CComHeapPtr`オブジェクト。 そうである場合、新しい`CComHeapPtr`オブジェクトを新しいポインターとリソースを管理する責任を前提としています。

## <a name="see-also"></a>関連項目

[CHeapPtr クラス](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase クラス](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator クラス](../../atl/reference/ccomallocator-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
