---
title: OLE DB Provider で文字列を格納する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75f845027e5c629fe61b8cca6ab3f23306aa57bf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053228"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>OLE DB プロバイダーへの文字列の格納

ATL OLE DB プロバイダー ウィザードが既定のユーザー レコードを作成する CustomRS.h、`CWindowsFile`します。 2 つの文字列を処理するために変更するか`CWindowsFile`または次のコードに示すように、ユーザー レコードを追加します。

```cpp
////////////////////////////////////////////////////////////////////////
class CAgentMan:
   public WIN32_FIND_DATA
   DWORD dwBookmark;              // Add this
   TCHAR szCommand[256];          // Add this
   TCHAR szText[256];             // Add this
   TCHAR szCommand2[256];         // Add this
   TCHAR szText2[256];            // Add this

{
public:
BEGIN_PROVIDER_COLUMN_MAP()
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)
END_PROVIDER_COLUMN_MAP()
   bool operator==(const CAgentMan& am) // This is optional
   {
      return (lstrcmpi(cFileName, wf.cFileName) == 0);
   }
};
```

データ メンバー`szCommand`と`szText`で 2 つの文字列を表す`szCommand2`と`szText2`必要な場合、追加の列を提供します。 データ メンバー`dwBookmark`この単純な読み取り専用プロバイダーは必要ありませんが、後で追加に使用されます、`IRowsetLocate`インターフェイスは、参照してください[、単純な読み取り専用プロバイダーの強化](../../data/oledb/enhancing-the-simple-read-only-provider.md)します。 `==`演算子とインスタンスを比較します (この演算子の実装は省略可能)。

これが完了したら、プロバイダーをコンパイルして実行する準備があります。 プロバイダーをテストするには、照合機能を持つコンシューマーが必要です。 [単純なコンシューマーを実装する](../../data/oledb/implementing-a-simple-consumer.md)テストのコンシューマーを作成する方法を示しています。 プロバイダーとコンシューマー テストを実行します。 クリックすると、テストのコンシューマーがプロバイダーから適切な文字列を取得することを確認、**実行**ボタン、**テスト コンシューマー**  ダイアログ ボックス。

ご利用のプロバイダーのテストが成功する場合は、追加のインターフェイスを実装することでその機能を強化するために可能性があります。 例に示した[単純な読み取り専用プロバイダーの強化](../../data/oledb/enhancing-the-simple-read-only-provider.md)します。

## <a name="see-also"></a>関連項目

[単純な読み取り専用プロバイダーの実装](../../data/oledb/implementing-the-simple-read-only-provider.md)