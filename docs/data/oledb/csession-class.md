---
title: CSession クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 920ad8c48846396741d0ee2feb01855bd3b927d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063784"
---
# <a name="csession-class"></a>CSession クラス

1 つのデータベース アクセスのセッションを表します。

## <a name="syntax"></a>構文

```cpp
class CSession
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[Abort](#abort)|キャンセル (終了) トランザクション。|
|[閉じる](#close)|セッションを閉じます。|
|[コミット](#commit)|トランザクションをコミットします。|
|[GetTransactionInfo](#gettransactioninfo)|トランザクションに関する情報を返します。|
|[開く](#open)|データ ソース オブジェクトの新しいセッションを開きます。|
|[StartTransaction](#starttransaction)|このセッション用の新しいトランザクションを開始します。|

## <a name="remarks"></a>Remarks

各プロバイダー接続 (データ ソース) で表される 1 つまたは複数のセッションを関連付けることができます、 [CDataSource](../../data/oledb/cdatasource-class.md)オブジェクト。 新たに作成する`CSession`の`CDataSource`、呼び出す[csession::open](../../data/oledb/csession-open.md)します。 データベースのトランザクションを開始する`CSession`提供、`StartTransaction`メソッド。 トランザクションが開始されるを使用してコミットすることができます、`Commit`メソッド、またはキャンセルを使用して、`Abort`メソッド。

## <a name="abort"></a> Csession::abort

トランザクションを終了します。

### <a name="syntax"></a>構文

```cpp
HRESULT Abort(BOID* pboidReason = NULL, 
   BOOL bRetaining = FALSE, 
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[itransaction::abort](/previous-versions/windows/desktop/ms709833)で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="close"></a> Csession::close

によって開かれたセッションを閉じます[csession::open](../../data/oledb/csession-open.md)します。

### <a name="syntax"></a>構文

```cpp
void Close() throw();
```

### <a name="remarks"></a>Remarks

リリース、`m_spOpenRowset`ポインター。

## <a name="commit"></a> Csession::commit

トランザクションをコミットします。

### <a name="syntax"></a>構文

```cpp
HRESULT Commit(BOOL bRetaining = FALSE, 
   DWORD grfTC = XACTTC_SYNC, 
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[itransaction::commit](/previous-versions/windows/desktop/ms713008)で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [itransaction::commit](/previous-versions/windows/desktop/ms713008)します。

## <a name="gettransactioninfo"></a> Csession::gettransactioninfo

トランザクションに関する情報を返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975)で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="open"></a> Csession::open

データ ソース オブジェクトの新しいセッションを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>パラメーター

*ds*<br/>
[in]データ ソースは、セッションが開かれているのです。

*pPropSet*<br/>
[in]配列へのポインター [DBPROPSET](/previous-versions/windows/desktop/ms714367)プロパティおよび設定する値を含む構造体。 参照してください[プロパティ セットとプロパティ グループ](/previous-versions/windows/desktop/ms713696)で、 *OLE DB プログラマーズ リファレンス*Windows SDK にします。

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367)構造体が渡された、 *pPropSet*引数。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

使用してデータ ソース オブジェクトを開く必要があります[cdatasource::open](../../data/oledb/cdatasource-open.md)に渡す前に`CSession::Open`します。

## <a name="starttransaction"></a> Csession::starttransaction

このセッション用の新しいトランザクションを開始します。

### <a name="syntax"></a>構文

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[itransactionlocal::starttransaction](/previous-versions/windows/desktop/ms709786)で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [itransactionlocal::starttransaction](/previous-versions/windows/desktop/ms709786)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="see-also"></a>関連項目

[CatDB](../../visual-cpp-samples.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)