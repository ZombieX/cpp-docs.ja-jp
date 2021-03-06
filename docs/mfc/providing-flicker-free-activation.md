---
title: ちらつきなしのアクティベーションの提供 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9f780472b8256f6d8332ecbde08138d85c8ebd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378328"
---
# <a name="providing-flicker-free-activation"></a>ちらつきなしのアクティベーションの提供

コントロール、非アクティブとアクティブの状態で同一の描画 (およびウィンドウなしのアクティベーションを使用しない) 場合に、描画操作と、非アクティブの間で移行するときに通常発生するちらつきを除外できます。およびアクティブ状態です。 これを行うには、 **noFlickerActivate**フラグによって返される一連のフラグ[オン](../mfc/reference/colecontrol-class.md#getcontrolflags)します。 例えば:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

選択した場合、このフラグを追加するコードが自動的に生成、**ちらつきなしのアクティベーション**オプションを[コントロール設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX コントロール ウィザードを使用して、コントロールを作成するときのページします。

ウィンドウなしのアクティベーションを使用している場合は、この最適化に影響はありません。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)

