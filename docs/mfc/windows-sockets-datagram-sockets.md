---
title: 'Windows ソケット: データグラム ソケット |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a63caa786ce5198fb902b8d48101507fb2b4113
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444217"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows ソケット : データグラム ソケット

この記事では、データグラム ソケットでは、使用できる 2 つの Windows ソケット型のいずれかについて説明します。 (その他の型は、[ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md))。

データグラム ソケットをシーケンス処理または重複しないことが保証される双方向データ フローをサポートします。 データグラムが信頼性保証はされませんも受信に失敗したことができます。 データグラム データが到着順不同のおよび場合によって重複が、レコードが、受信側のサイズが内部制限よりも小さい場合に限り、データ内のレコードの境界を保持します。 シーケンス処理と信頼性の管理を担当します。 (信頼性はローカル エリア ネットワーク (LAN) で適切になる傾向がありますが以下でワイド エリア ネットワーク (WAN)、インターネットなど)。

データグラムは「コネクションレス」、つまり、明示的な接続は確立されません。指定したソケットにデータグラム メッセージを送信して、指定したソケットからメッセージを受信できます。

データグラム ソケットの例は、同期されているネットワーク上のシステム クロックを維持するアプリケーションです。 これは、データグラム ソケットで少なくとも一部の設定の追加機能を示しています。 大量のネットワーク アドレスにメッセージをブロードキャストします。

データグラム ソケットは、データのレコード指向ストリーム ソケットよりも優れていますが。 データグラム ソケットの詳細については、Windows SDK で利用できる Windows ソケット仕様を参照してください。

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)

