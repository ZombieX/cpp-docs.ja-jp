---
title: IAccessorImpl クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89762d37977efd4c999c38ee9bc586420655f1cc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078363"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl クラス

実装を提供、 [IAccessor](/previous-versions/windows/desktop/ms719672)インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
行セットまたはコマンドのオブジェクト クラス。

*BindType*<br/>
バインド情報のストレージ ユニット。 既定値は、`ATLBINDINGS`構造 (atldb.h を参照してください)。

*BindingVector*<br/>
列情報のストレージ ユニット。 既定値は[CAtlMap](../../atl/reference/catlmap-class.md) 、重要な要素は HACCESSOR 値を値要素へのポインター、`BindType`構造体。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|コンストラクターです。|

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|既存のアクセサーには、参照カウントを追加します。|
|[CreateAccessor](#createaccessor)|バインドのセットからアクセサーを作成します。|
|[GetBindings](#getbindings)|アクセサーのバインディングを返します。|
|[ReleaseAccessor](#releaseaccessor)|アクセサーを解放します。|

## <a name="remarks"></a>Remarks

これは、機能は、行セットおよびコマンドに必須です。 OLE DB、HACCESSOR を実装するプロバイダーを必要とタグの配列をある[DBBINDING](/previous-versions/windows/desktop/ms716845)構造体。 によって提供される HACCESSORs`IAccessorImpl`のアドレス、`BindType`構造体。 既定では、`BindType`として定義されている場合は、`ATLBINDINGS`で`IAccessorImpl`のテンプレートの定義。 `BindType` 使用されるメカニズムを提供します。`IAccessorImpl`内の要素の数を追跡するためにその`DBBINDING`参照カウントおよびアクセサーのフラグと配列。

## <a name="iaccessorimpl"></a> Iaccessorimpl::iaccessorimpl

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> Iaccessorimpl::addrefaccessor

既存のアクセサーには、参照カウントを追加します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>パラメーター

参照してください[IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="createaccessor"></a> Iaccessorimpl::createaccessor

バインドのセットからアクセサーを作成します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[iaccessor::createaccessor](/previous-versions/windows/desktop/ms720969)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="getbindings"></a> Iaccessorimpl::getbindings

アクセサーのコンシューマーからの列の基本的なバインディングを返します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>パラメーター

参照してください[IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="releaseaccessor"></a> Iaccessorimpl::releaseaccessor

アクセサーを解放します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>パラメーター

参照してください[iaccessor::releaseaccessor](/previous-versions/windows/desktop/ms719717)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)