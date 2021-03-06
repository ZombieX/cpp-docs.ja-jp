---
title: ダイアログ リソースの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c68f8f48ec08446a9fca20524a8309b041607a92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401590"
---
# <a name="creating-the-dialog-resource"></a>ダイアログ リソースの作成

デザイン、 [ ダイアログ ボックス](../mfc/dialog-boxes.md)ダイアログ リソースを作成を使用して、[ダイアログ エディター](../windows/dialog-editor.md)。 ダイアログ エディターでは、次のことができます。

- 表示されたら、ダイアログ ボックスがある場所とサイズを調整します。

- コントロールのパレットからさまざまな種類のコントロールをドラッグし、ダイアログ ボックスで必要な場所にドロップします。

- ツールバーのボタンの配置を持つコントロールを位置します。

- プログラムでが動作と外観をシミュレートすることで、ダイアログ ボックスをテストします。 テスト モードでは、テキスト ボックスにテキストを入力して、プッシュ ボタンをクリックするとダイアログ ボックスのコントロールを操作しにできます。

完了したら、ダイアログ テンプレート リソースは、アプリケーションのリソース スクリプト ファイルに格納されます。 編集できますが後で必要な場合。 作成し、ダイアログ リソースを編集する方法の詳細については、次を参照してください。、[ダイアログ エディター](../windows/dialog-editor.md)トピック。 この手法は、のダイアログ テンプレート リソースの作成にも使用[CFormView](../mfc/reference/cformview-class.md)と[CRecordView](../mfc/reference/crecordview-class.md)クラス。

ダイアログ ボックスの外観はきっと、ダイアログ クラスを作成し、で説明したように、そのメッセージをマップ[コード ウィザードによるダイアログ クラスの作成](../mfc/creating-a-dialog-class-with-code-wizards.md)です。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[ダイアログ ボックスの有効期間](../mfc/life-cycle-of-a-dialog-box.md)

