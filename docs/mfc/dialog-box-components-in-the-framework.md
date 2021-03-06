---
title: フレームワークのダイアログ ボックス コンポーネント |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6936a48d1a3e1845d56c73524c84800d9d605155
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065513"
---
# <a name="dialog-box-components-in-the-framework"></a>フレームワークのダイアログ ボックス コンポーネント

MFC フレームワークでは、ダイアログ ボックスは 2 つのコンポーネントがあります。

- ダイアログ ボックスのコントロールとその配置を指定するダイアログ テンプレート リソースです。

   ダイアログ リソースでは、元の Windows がダイアログ ウィンドウを作成し、表示するダイアログ テンプレートを格納します。 テンプレートには、サイズ、場所、スタイル、種類、ダイアログ ボックスのコントロールの位置など、ダイアログ ボックスの特性を指定します。 リソースとして格納されているダイアログ テンプレートを使用することは、通常は、メモリ内で、独自のテンプレートを作成することもできます。

- ダイアログ クラスから派生した[CDialog](../mfc/reference/cdialog-class.md)、ダイアログ ボックスを管理するためのプログラム インターフェイスを提供します。

   ダイアログ ボックスでは、ウィンドウし、表示される場合は、Windows ウィンドウにアタッチされます。 ダイアログ ウィンドウが作成されたときにダイアログ テンプレート リソースは、ダイアログ ボックスのウィンドウ コントロールの子を作成するため、テンプレートとして使用されます。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[ダイアログ ボックスの有効期間](../mfc/life-cycle-of-a-dialog-box.md)

