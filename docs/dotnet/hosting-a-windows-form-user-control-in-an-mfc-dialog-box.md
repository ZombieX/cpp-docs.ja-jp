---
title: MFC ダイアログ ボックスでユーザー コントロールをフォーム、Windows のホスト |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a1f2c042c1a4a97bc322a61cadccbd60d2a570ea
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392308"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>MFC ダイアログ ボックスにおける Windows フォーム ユーザー コントロールのホスト

MFC ActiveX コントロールの特別な種類として、Windows フォーム コントロールをホストし、ActiveX インターフェイス、およびプロパティとメソッドを使用して、コントロールと通信、<xref:System.Windows.Forms.Control>クラス。 .NET Framework のプロパティとメソッドを使用するコントロールを操作することをお勧めします。

Windows フォームと MFC を示すサンプル アプリケーションの場合、次を参照してください。 [MFC と Windows フォーム統合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)します。

> [!NOTE]
>  現在のリリースで、`CDialogBar`オブジェクトは、Windows フォーム コントロールをホストできません。

## <a name="in-this-section"></a>このセクションの内容

[方法: ダイアログ ボックスにユーザー コントロールおよびホストを作成する](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[方法: Windows フォームで DDX/DDV データ バインディング](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[方法: ネイティブ C++ クラスから Windows フォーム イベントをシンクする](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>参照

[CWinFormsControl クラス](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog クラス](../mfc/reference/cdialog-class.md) &#124; [CWnd クラス](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>関連項目

[MFC での Windows フォーム ユーザー コントロールの使用](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows フォームと MFC のプログラミング上の違い](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[MFC ビューとしての Windows フォーム ユーザー コントロールのホスト](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[MFC ダイアログ ボックスとしての Windows フォーム ユーザー コントロールのホスト](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)