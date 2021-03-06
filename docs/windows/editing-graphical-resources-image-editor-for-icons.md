---
title: グラフィカル リソース (アイコン用イメージ エディターを C++) の編集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- images [C++], editing
- graphics [C++]
- images [C++]
- Image editor [C++], about Image editor
- graphics [C++], Image editor
- graphics [C++], editing
ms.assetid: 09e422c5-f712-4378-b973-c7a3bbc92b9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7ff12ccf3868aac6189c749cc96c31046939c34
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072929"
---
# <a name="editing-graphical-resources-c-image-editor-for-icons"></a>グラフィカル リソースの編集 (アイコン用イメージ エディターを C++)

グラフィカル リソースは、アプリケーション用に定義したイメージです。 フリーハンドの描画または図形を使用して描画できます。 編集、反転、またはサイズ変更、イメージの一部を選択またはイメージの選択したパーツからカスタム ブラシを作成してそのブラシを使用して描画します。 画像のプロパティを定義、異なる形式で画像を保存、およびイメージの 1 つの形式から変換することができます。

新しいグラフィカルのリソースを作成するだけでなくすることができます[既存イメージをインポート](../windows/how-to-import-and-export-resources.md)を編集するため、プロジェクトに追加しています。 開いて編集するためのプロジェクトの一部ではないイメージ[スタンドアロン画像編集](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)します。

- [新しいビットマップまたはその他のイメージの作成](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)

- [選択して、描画ツールの使用](using-a-drawing-tool-image-editor-for-icons.md)

- [描画線または閉じた図形](../windows/drawing-lines-or-closed-figures-image-editor-for-icons.md)

- [イメージの領域の選択](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)

- [選択した一部のイメージの編集](../windows/editing-parts-of-an-image-image-editor-for-icons.md)

- [イメージの回転](../windows/flipping-an-image-image-editor-for-icons.md)

- [イメージのサイズ変更](../windows/resizing-an-image-image-editor-for-icons.md)

- [カスタム ブラシの作成](../windows/creating-a-custom-brush-image-editor-for-icons.md)

- [画像のプロパティを変更します。](changing-image-properties-image-editor-for-icons.md)

- [.Gifs または .jpegs ビットマップの保存](../windows/saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons.md)

- [イメージの 1 つの形式を変換します。](../windows/converting-an-image-from-one-format-to-another-image-editor-for-icons.md)

- [プロジェクトの外側でのイメージの編集](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)

- [[イメージ] メニュー](../windows/image-menu-image-editor-for-icons.md)

- [イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)

- [イメージ エディター ウィンドウ](../windows/window-panes-image-editor-for-icons.md)

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

> [!NOTE]
> 使用して、**イメージ エディター**、32 ビットのイメージを表示することができますが、編集することはできません。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)