---
title: ウィンドウ プロシージャ エントリ ポイント |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3226df51d2a83484de78d0d76c9af67e150e8eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403189"
---
# <a name="window-procedure-entry-points"></a>ウィンドウ プロシージャのエントリ ポイント

MFC のウィンドウ プロシージャ、特別なウィンドウ プロシージャの実装を含むモジュールの静的リンクを保護します。 MFC のモジュールがリンクされている場合、リンケージは自動的に発生します。 このウィンドウの手順では、AFX_MANAGE_STATE マクロを使用して、有効なモジュールの状態が正しく設定し、呼び出す`AfxWndProc`、順番にデリゲートを`WindowProc`メンバー関数は、適切な`CWnd`-派生オブジェクト。

## <a name="see-also"></a>関連項目

[MFC モジュールの状態データの管理](../mfc/managing-the-state-data-of-mfc-modules.md)

