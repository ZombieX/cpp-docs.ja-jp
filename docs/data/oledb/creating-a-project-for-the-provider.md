---
title: プロバイダーのプロジェクトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f4049190ac30cfff634d4cfef82410ccfdf1314
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063082"
---
# <a name="creating-a-project-for-the-provider"></a>プロバイダーのプロジェクトの作成

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>OLE DB プロバイダーが存在するプロジェクトを作成するには

1. **[ファイル]** メニューの **[新規作成]** をクリックし、**[プロジェクト]** をクリックします。

   **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

1. **プロジェクトの種類**ウィンドウで、をクリックして、**インストール済み** > **Visual C** > **MFC/ATL**フォルダー。 **テンプレート**ウィンドウで、をクリックして**ATL プロジェクト**します。

    > [!NOTE]
    > Visual Studio の以前のバージョンで、プロジェクトの種類を検索**インストール済み** > **テンプレート** > **Visual C**  > **ATL**します。

1. **名前**ボックスに、プロジェクトの名前を入力し、 をクリックして**OK**します。

   **ATL プロジェクト ウィザード**が表示されます。

1. **ATL プロジェクト ウィザード**、選択**ダイナミック リンク ライブラリ (DLL)** の**アプリケーションの種類**します。

1. **[完了]** をクリックします。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)