---
title: ヘッダー コントロール通知の処理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd7c6fa8a85aee06aca3b1bf804a06df428e82cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387758"
---
# <a name="processing-header-control-notifications"></a>ヘッダー コントロール通知の処理

ビューまたはダイアログ クラスで作成するプロパティ ウィンドウを使用して、 [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)ハンドラー関数のヘッダー コントロールの switch ステートメントを ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) にする通知メッセージ処理 (を参照してください[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md))。 ユーザーをクリックするか、項目との間の区分線をドラッグが、ヘッダー項目をダブルクリックしたときに、親ウィンドウに通知が送信されます。

ヘッダー コントロールに関連付けられている通知メッセージに記載されて[ヘッダー コントロールのリファレンス](https://msdn.microsoft.com/library/windows/desktop/bb775239)Windows SDK に含まれています。

## <a name="see-also"></a>関連項目

[CHeaderCtrl の使い方](../mfc/using-cheaderctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)

