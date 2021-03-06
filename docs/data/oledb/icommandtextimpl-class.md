---
title: ICommandTextImpl クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2ddd7e1a4397b36daba8b354c84941d0d1c4d0e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057973"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl クラス

実装を提供、 [ICommandText](/previous-versions/windows/desktop/ms714914)インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
コマンド クラスから派生した`ICommandTextImpl`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** altdb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[GetCommandText](#getcommandtext)|テキスト コマンドの最後の呼び出しでセットを返します[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)します。|
|[SetCommandText](#setcommandtext)|既存のコマンド テキストを置き換えて、コマンド テキストを設定します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_strCommandText](#strcommandtext)|コマンド テキストを格納します。|

## <a name="remarks"></a>Remarks

コマンドの必須インターフェイス。

## <a name="getcommandtext"></a> Icommandtextimpl::getcommandtext

テキスト コマンドの最後の呼び出しでセットを返します[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect, 
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>パラメーター

参照してください[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825)で、 *OLE DB プログラマーズ リファレンス*します。 *既定で*パラメーターは既定では無視されます。

## <a name="setcommandtext"></a> Icommandtextimpl::setcommandtext

既存のコマンド テキストを置き換えて、コマンド テキストを設定します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect, 
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>パラメーター

参照してください[icommandtext::setcommandtext](/previous-versions/windows/desktop/ms709757)で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="strcommandtext"></a> Icommandtextimpl::m_strcommandtext

コマンド テキストの文字列を格納します。

### <a name="syntax"></a>構文

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)