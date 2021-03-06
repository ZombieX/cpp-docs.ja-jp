---
title: CCustomCommand (CustomRS.H) |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cf78ca4fc15179671ecc8df4843514ac4e65aa1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067253"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand`クラスは、プロバイダー コマンド オブジェクトの実装。 実装を提供しますが、 `IAccessor`、 `ICommandText`、および`ICommandProperties`インターフェイス。 `IAccessor`インターフェイスは、行セットの 1 つと同じです。 コマンド オブジェクトでは、アクセサーを使用して、バインド パラメーターを指定します。 行セット オブジェクトでは、出力列のバインドを指定するのに、それらを使用します。 `ICommandText`インターフェイスは、テキスト コマンドを指定する便利な方法です。 この例では、`ICommandText`インターフェイスの後でカスタム コードを追加する場合もオーバーライド、`ICommand::Execute`メソッド。 `ICommandProperties`インターフェイスはすべてのコマンドと行セット オブジェクトのプロパティを処理します。

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

`IAccessor`インターフェイス コマンドと行セットで使用されるすべてのバインドを管理します。 コンシューマーは`IAccessor::CreateAccessor`の配列で`DBBINDING`構造体。 各`DBBINDING`構造には (型と長さ) などの列バインドの処理方法に関する情報が含まれています。 プロバイダーは、構造体を受け取り、データの転送方法と、すべての変換が必要かどうかを判断します。 `IAccessor`インターフェイスが、コマンドのパラメーターを処理するために、コマンド オブジェクトで使用します。

コマンド オブジェクトは、の実装も用意されています。`IColumnsInfo`します。 OLE DB 必要があります、`IColumnsInfo`インターフェイス。 インターフェイスは、コマンドのパラメーターに関する情報を取得するコンシューマーを使用します。 行セット オブジェクトを使用して、`IColumnsInfo`プロバイダーに出力する列についての情報を返すインターフェイス。

プロバイダーは、というインターフェイスも含まれています。`IObjectWithSite`します。 `IObjectWithSite`インターフェイスは、ATL 2.0 で実装されたでき、その子にそれ自体に関する情報を渡す、実装者。 コマンド オブジェクトを使用して、`IObjectWithSite`いずれかを指示する情報は、それらを作成したユーザーについての行セット オブジェクトを生成します。

## <a name="see-also"></a>関連項目

[プロバイダー ウィザードで生成されたファイル](../../data/oledb/provider-wizard-generated-files.md)