---
title: 別の言語 (C++) のバージョン情報の追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97ad11f7982fd5a413c6740fe969c5edc20636a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389383"
---
# <a name="adding-version-information-for-another-language-c"></a>別の言語 (C++) のバージョン情報の追加

### <a name="to-add-version-information-for-another-language-new-info-block"></a>別の言語のバージョン情報 (新しい情報ブロック) を追加するには

1. [[リソース ビュー]](../windows/resource-view-window.md)でバージョン情報リソースをダブルクリックして開きます。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

2. バージョン情報のテーブル内で右クリックし、ショートカット メニューから **[新しいバージョン情報ブロック]** を選びます。

   このコマンドを使用して、現在のバージョン情報リソースにさらに情報ブロックを追加し、それに対応するプロパティを [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で開きます。

3. **[プロパティ]** ウィンドウで、新しいブロック用の適切な言語と文字セットを選びます。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>要件

Win32

## <a name="see-also"></a>関連項目

[バージョン エディター](../windows/version-information-editor.md)<br/>
[バージョン情報 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)