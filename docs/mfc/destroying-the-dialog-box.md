---
title: ダイアログ ボックスの破棄 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 863b70f3bf4e9828d69024b838dce43abbba26be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425913"
---
# <a name="destroying-the-dialog-box"></a>ダイアログ ボックスの破棄

モーダル ダイアログ ボックスは通常、スタック フレーム上に作成し、それを作成した関数が終了するたびに破棄します。 オブジェクトがスコープ外になるダイアログ オブジェクトのデストラクターが呼び出されます。

モードレス ダイアログ ボックスが通常作成され、親ビューまたはフレーム ウィンドウが所有する、アプリケーションのメイン フレーム ウィンドウまたはドキュメント フレーム ウィンドウ。 既定の[OnClose](../mfc/reference/cwnd-class.md#onclose)ハンドラー呼び出し[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)、ダイアログ ボックス ウィンドウを破棄します。 オーバーライドする場合、ダイアログ ボックスがスタンドアロンでないポインター、またはその他の特殊な所有権セマンティクスであり、 [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) C++ ダイアログ オブジェクトを破棄します。 オーバーライドする必要がありますも[OnCancel](../mfc/reference/cdialog-class.md#oncancel)を呼び出すと`DestroyWindow`からそこ。 それ以外の場合は、ダイアログ ボックスのオーナーが必要でなくなったときに C++ オブジェクトを破棄する必要があります。

## <a name="see-also"></a>関連項目

[ダイアログ ボックスの有効期間](../mfc/life-cycle-of-a-dialog-box.md)

