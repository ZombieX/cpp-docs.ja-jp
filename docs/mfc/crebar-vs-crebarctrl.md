---
title: CReBar とCrebarctrl の比較 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133e298cd0bc5b497fbbba47982a755afeefb2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442852"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar とCReBarCtrl

MFC には、rebars を作成する 2 つのクラスが用意されています: [CReBar](../mfc/reference/crebar-class.md)と[crebarctrl の比較](../mfc/reference/crebarctrl-class.md)(ラップしています。 Windows のコモン コントロール API)。 `CReBar` すべての共通の rebar コントロールの機能を提供しますが、必要な一般的なコントロールの設定と構造体の多くを処理します。

`CReBarCtrl` Win32 rebar コントロールのラッパー クラスは、そのため、MFC のアーキテクチャに rebar を統合する予定がない場合の実装が簡単にあります。 使用して行う場合`CReBarCtrl`と MFC アーキテクチャに rebar を統合、rebar コントロールの操作 (MFC に) を通信するためにさらに注意を行う必要があります。 この通信は困難です。ただしは、使用すると、必要な追加の作業が`CReBar`します。

Visual C には、rebar の一般的なコントロールを活用するために 2 つの方法が用意されています。

- 使用して、rebar の作成`CReBar`を呼び出して[CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl)へのアクセスを取得する、`CReBarCtrl`メンバー関数。

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` キャストするインライン メンバー関数は、**この**rebar オブジェクトのポインター。 つまり、実行時に、関数呼び出しのオーバーヘッドが発生しません。

- 使用して、rebar の作成[crebarctrl の比較](../mfc/reference/crebarctrl-class.md)のコンス トラクター。

いずれかの方法、rebar コントロールのメンバー関数へアクセスは許可されます。 呼び出すと`CReBar::GetReBarCtrl`への参照を返します、`CReBarCtrl`オブジェクト メンバー関数のいずれかのセットを使用できるようにします。 参照してください[CReBar](../mfc/reference/crebar-class.md)を構築してを使用して、rebar の作成について`CReBar`します。

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)

