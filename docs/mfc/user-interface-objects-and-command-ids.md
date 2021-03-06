---
title: ユーザー インターフェイス オブジェクトとコマンド Id |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8a61699ddd2c48e36bdfd5936fb4ab7aa56e0a9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416124"
---
# <a name="user-interface-objects-and-command-ids"></a>ユーザー インターフェイス オブジェクトとコマンド ID

メニュー項目、ツール バー ボタン、およびアクセラレータ キーが「ユーザー インターフェイス オブジェクト」コマンドを生成できます。 このような各ユーザー インターフェイス オブジェクトが ID コマンド オブジェクトとコマンドを同じ ID を割り当てることで、ユーザー インターフェイス オブジェクトに関連付けます。 説明したよう[メッセージ](../mfc/messages.md)コマンドは、特別なメッセージとして実装されます。 「コマンド フレームワーク内の」次の図は、フレームワークがコマンドを管理する方法を示します。 ときに、コマンドを生成、ユーザー インターフェイス オブジェクトなど`ID_EDIT_CLEAR_ALL`は、アプリケーション内のオブジェクトのいずれかのコマンドを処理する-ドキュメント オブジェクトの次の図の`OnEditClearAll`ドキュメントのメッセージ マップを使用して関数が呼び出されます。

![フレームワークにおけるコマンド](../mfc/media/vc385p1.gif "vc385p1")フレームワーク内のコマンド

「コマンド更新フレームワーク内の」次の図は、MFC がメニュー項目とツール バー ボタンなどのユーザー インターフェイス オブジェクトを更新する方法を示します。 メニューになると停止、またはツール バー ボタンの場合、アイドル ループの中に、前に、MFC は、update コマンドをルーティングします。 ドキュメント オブジェクトがその更新コマンド ハンドラーを呼び出す次の図に`OnUpdateEditClearAll`を有効にまたはユーザー インターフェイス オブジェクトを無効にします。

![コマンド更新フレームワークで](../mfc/media/vc385p2.png "vc385p2")フレームワークでコマンドを更新しています

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)

