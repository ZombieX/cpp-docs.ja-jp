---
title: 追加時にコントロールをサイズ変更 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: 06b1dd2b-0ba1-4e1f-adc3-cb73679f765e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e60803ec9696e541376aa8530cb4c01d32b9e569
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418862"
---
# <a name="sizing-a-control-while-you-add-it"></a>コントロールの追加時のサイズ変更

### <a name="to-size-a-control-while-you-add-it"></a>追加するコントロールのサイズ

1. コントロールを選び、[ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox)します。

2. ダイアログ ボックスで、新しいコントロールの左上隅となる (これに十字が表示されます)、カーソルを置きます。

3. をクリックし、ダイアログ ボックスで、コントロールの左上隅に固定するマウス ボタンを押しながら、目的のサイズになるまで、右、下にカーソルをドラッグします。

   > [!NOTE]
   > 実際に描画するコントロールの四隅のいずれかを固定できます。 この手順では、例として、左上隅にあるを使用します。

4. マウスのボタンを離します。 指定したサイズでダイアログ ボックスにコントロールが配置されます。

   > [!TIP]
   > コントロールのサイズを変更するには、コントロールの境界線にサイズ変更ハンドルを移動することによって、ダイアログ ボックスの上にドロップするとします。 詳細については、次を参照してください。[個々 のコントロールをサイズ変更](../windows/sizing-individual-controls.md)します。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>要件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[ダイアログ ボックス コントロールへのイベント ハンドラーの追加](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[ダイアログ ボックス コントロールおよび変数の型](../ide/dialog-box-controls-and-variable-types.md)