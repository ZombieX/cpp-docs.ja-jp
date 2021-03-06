---
title: CArrayRowset クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b8613372b84423a14fd995d78ca9d4c0dd1c1ae
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070381"
---
# <a name="carrayrowset-class"></a>CArrayRowset クラス

配列の構文を使用して行セットの要素をアクセスします。

## <a name="syntax"></a>構文

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>, 
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>パラメーター

*TAccessor*<br/>
行セットで使用するアクセサー クラスの型。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CArrayRowset](#carrayrowset)|コンストラクターです。|
|[スナップショット](#snapshot)|行セット全体をメモリに読み込みます。|

### <a name="operators"></a>演算子

|||
|-|-|
|[演算子&#91;&#93;](#operator)|行セットの要素にアクセスします。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|既に読み取られた行の数。|

## <a name="carrayrowset"></a> Carrayrowset::carrayrowset

新しい `CArrayRowset` オブジェクトを作成します。

### <a name="syntax"></a>構文

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>パラメーター

*nMax*<br/>
[in]行セットの行の最大数。

## <a name="snapshot"></a> Carrayrowset::snapshot

メモリ、イメージまたはそのスナップショットを作成するのには、行セット全体を読み取ります。

### <a name="syntax"></a>構文

```cpp
HRESULT Snapshot() throw();
```

## <a name="operator"></a> Carrayrowset:

行セット内の行にアクセスするためには、配列に似た構文を提供します。

### <a name="syntax"></a>構文

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>パラメーター

*TAccessor*<br/>
行セットに格納されているアクセサーの種類を指定するテンプレート パラメーター。

*nRow*<br/>
[in] (配列) にアクセスする、行の数です。

### <a name="return-value"></a>戻り値

要求された行の内容。

### <a name="remarks"></a>Remarks

場合*nRow*行セットの行の数を超える、例外がスローされます。

## <a name="nrowsread"></a> Carrayrowset::m_nrowsread

既に読み取られた行セット内の行の数が含まれています。

### <a name="syntax"></a>構文

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset クラス](../../data/oledb/crowset-class.md)