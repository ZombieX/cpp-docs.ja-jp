---
title: プロバイダーの作成 |Microsoft Docs
ms.custom: ''
ms.date: 10/15/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 230620a2375ac5aa822e55496d1f26751ee6f7b3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055347"
---
# <a name="creating-the-provider"></a>プロバイダーの作成

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>ATL OLE DB プロバイダー ウィザードで、OLE DB プロバイダーを作成するには

1. プロジェクトで右クリックします。

1. ショートカット メニューで、**追加**、 をクリックし、**クラスの追加**します。

1. **クラスの追加**ダイアログ ボックスで、**インストール済み** > **Visual C** > **ATL**、選択、 **ATL OLEDB プロバイダー**アイコン、およびクリック**オープン**します。

1. **ATL OLE DB プロバイダー ウィザード**で、プロバイダーの短い名前を入力、**短い名前**ボックス。 次のトピックを使用して、短い名前*カスタム*が、別の名前を使用することができます。 他の名前ボックスは、入力した名前に基づいて設定します。

1. 必要な場合は、また、他の名前を編集します。 オブジェクトとファイル名だけでなく、次のように編集できます。

   - **コクラス**: COM を使用して、プロバイダーを作成する名前。

   - **ProgID**: プログラムの id は、GUID の代わりに使用できるテキスト文字列です。

   - **バージョン**: コクラスと ProgID とバージョンに依存するプログラム ID を生成するために使用

1. **[完了]** をクリックします。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)
