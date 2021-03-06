---
title: Run メンバー関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 446b1b6fc2a5265e2c4eb8a608ff8b4f0028c57d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408233"
---
# <a name="run-member-function"></a>Run メンバー関数

Framework アプリケーションのほとんどの時間内に費やす、[実行](../mfc/reference/cwinapp-class.md#run)クラスのメンバー関数[CWinApp](../mfc/reference/cwinapp-class.md)します。 初期化後、`WinMain`呼び出し`Run`メッセージ ループを処理します。

`Run` メッセージのループで使用可能なメッセージのメッセージ キューのチェックを切り替えます。 メッセージが、使用可能な場合は`Run`をディスパッチします。 これが true の場合、多くの場合、メッセージがない場合は、`Run`呼び出し`OnIdle`完了またはフレームワークを必要とするアイドル処理を実行します。 行うには、メッセージが表示されないとなしのアイドル処理がある場合は、アプリケーションは何かが発生するまで待機します。 アプリケーションが終了すると、`Run`呼び出し`ExitInstance`します。 図に[OnIdle メンバー関数](../mfc/onidle-member-function.md)メッセージ ループ内のアクションのシーケンスを示しています。

メッセージのディスパッチは、メッセージの種類によって異なります。 詳細については、次を参照してください。[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)します。

## <a name="see-also"></a>関連項目

[CWinApp: アプリケーション クラス](../mfc/cwinapp-the-application-class.md)
