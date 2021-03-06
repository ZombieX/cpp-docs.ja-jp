---
title: IDBPropertiesImpl クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fc27506657e1e2eeb7fdb7d0d5ef9147d5442dbc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060795"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl クラス

実装を提供、`IDBProperties`インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`IDBPropertiesImpl`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[GetProperties](#getproperties)|現在、データ ソース オブジェクトまたは現在に設定されている初期化プロパティ グループ内のプロパティの値に設定されているデータ ソース、データ ソースの情報、および初期化プロパティ グループ内のプロパティの値を返します、列挙子。|
|[GetPropertyInfo](#getpropertyinfo)|プロバイダーでサポートされているすべてのプロパティに関する情報を返します。|
|[SetProperties](#setproperties)|列挙子のデータ ソースと初期化プロパティ グループのデータ ソース オブジェクト、または、初期化プロパティ グループのプロパティを設定します。|

## <a name="remarks"></a>Remarks

[IDBProperties](/previous-versions/windows/desktop/ms719607)はデータ ソース オブジェクトに必要なインターフェイスと列挙子のオプションのインターフェイス。 ただし、列挙子を公開する場合[IDBInitialize](/previous-versions/windows/desktop/ms713706)、それを公開する必要があります`IDBProperties`します。 `IDBPropertiesImpl` 実装`IDBProperties`によって定義された静的関数を使用して[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)します。

## <a name="getproperties"></a> Idbpropertiesimpl::getproperties

現在、データ ソース オブジェクトまたは現在に設定されている初期化プロパティ グループ内のプロパティの値に設定されているデータ ソース、データ ソースの情報、および初期化プロパティ グループ内のプロパティの値を返します、列挙子。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets, 
   const DBPROPIDSET rgPropertySets[], 
   ULONG * pcProperties, 
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>パラメーター

参照してください[idbproperties::getproperties](/previous-versions/windows/desktop/ms714344)で、 *OLE DB プログラマーズ リファレンス*します。

いくつかのパラメーターに対応*OLE DB プログラマーズ リファレンス*で説明されている別の名前のパラメーター `IDBProperties::GetProperties`:

|OLE DB テンプレート パラメーター|*OLE DB プログラマーズ リファレンス*パラメーター|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Remarks

このメソッドがされた DBPROPSET_DATASOURCE、DBPROPSET_DATASOURCEINFO でのプロパティの値を返します、プロバイダーが初期化されている場合、データ ソース オブジェクトに現在設定されている DBPROPSET_DBINIT プロパティ グループ。 プロバイダーが初期化されていない場合は、DBPROPSET_DBINIT グループのプロパティのみを返します。

## <a name="getpropertyinfo"></a> Idbpropertiesimpl::getpropertyinfo

データ ソースでサポートされるプロパティの情報を返します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets, 
   const DBPROPIDSET rgPropertySets[], 
   ULONG * pcPropertyInfoSets, 
   DBPROPINFOSET ** prgPropertyInfoSets, 
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>パラメーター

参照してください[idbproperties::getpropertyinfo](/previous-versions/windows/desktop/ms718175)で、 *OLE DB プログラマーズ リファレンス*します。

いくつかのパラメーターに対応*OLE DB プログラマーズ リファレンス*で説明されている別の名前のパラメーター `IDBProperties::GetPropertyInfo`:

|OLE DB テンプレート パラメーター|*OLE DB プログラマーズ リファレンス*パラメーター|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Remarks

使用して[idbinitializeimpl::m_pcutlpropinfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)この機能を実装します。

## <a name="setproperties"></a> Idbpropertiesimpl::setproperties

列挙子のデータ ソースと初期化プロパティ グループのデータ ソース オブジェクト、または、初期化プロパティ グループのプロパティを設定します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets, 
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[idbproperties::setproperties](/previous-versions/windows/desktop/ms723049)で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="remarks"></a>Remarks

このメソッドがされた DBPROPSET_DATASOURCE、DBPROPSET_DATASOURCEINFO、のプロパティの値を設定する場合は、プロバイダーを初期化すると、データ ソース オブジェクトの DBPROPSET_DBINIT プロパティ グループ。 プロバイダーが初期化されていない場合は、DBPROPSET_DBINIT グループのプロパティのみを設定します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)