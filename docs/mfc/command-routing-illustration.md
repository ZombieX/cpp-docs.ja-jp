---
title: ルーティングの図にコマンド |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46449a90223bdb5e7774d4be5710014ff2c6ccae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406075"
---
# <a name="command-routing-illustration"></a>コマンド ルーティングの図

を示すために、MDI アプリケーションの編集] メニューの [すべてクリア メニュー項目からコマンド メッセージを検討してください。 このコマンドのハンドラー関数が、アプリケーションのドキュメント クラスのメンバー関数であるとします。 そのコマンドが、ユーザーがメニュー項目を選択した後にそのハンドラーをどのように到達する方法を次に示します。

1. メイン フレーム ウィンドウは、コマンド メッセージを最初に受け取ります。

1. メイン MDI フレーム ウィンドウは、現在アクティブな MDI 子ウィンドウにコマンドを処理する機会を与えます。

1. MDI 子フレーム ウィンドウの標準のルーティングにより、そのビューでのコマンドは、メッセージ マップを確認する前にできます。

1. ビューでは、まず、独自のメッセージ マップがチェックされ、関連付けられたドキュメントに、コマンドをルーティング次に、ハンドラーが見つからない。

1. ドキュメントは、メッセージ マップを確認し、ハンドラーを検索します。 このドキュメントのメンバー関数は呼び出され、ルーティングを停止します。

ドキュメントには、ハンドラーがないが、これは次にコマンドをルーティングはドキュメント テンプレートにします。 コマンドは、ビュー、フレーム ウィンドウに返します。 最後に、フレーム ウィンドウは、メッセージ マップを確認するは。 メイン MDI フレーム ウィンドウに戻ると、アプリケーション オブジェクトにコマンドをルーティングはもチェックに失敗した場合、ハンドルされていないコマンドの最終的な宛先。

## <a name="see-also"></a>関連項目

[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)

