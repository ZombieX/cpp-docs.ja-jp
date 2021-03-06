---
title: NCCALCSIZE_PARAMS 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6290c7600584f3225fee6cf9ed6a0f94373584c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413706"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS 構造体

`NCCALCSIZE_PARAMS`構造体には、アプリケーションは、サイズ、位置、およびウィンドウのクライアント領域の有効な内容を計算に WM_NCCALCSIZE メッセージの処理中に使用できることが含まれています。

## <a name="syntax"></a>構文

```
typedef struct tagNCCALCSIZE_PARAMS {
    RECT rgrc[3];
    PWINDOWPOS lppos;
} NCCALCSIZE_PARAMS;
```

#### <a name="parameters"></a>パラメーター

*rgrc*<br/>
四角形の配列を指定します。 最初には、移動またはサイズ変更が済んでいるウィンドウの新しい座標が含まれています。 2 つ目が移動またはサイズを変更する前に、ウィンドウの座標が含まれています。 3 つ目が移動またはサイズを変更する前に、ウィンドウのクライアント領域の座標が含まれています。 ウィンドウが子ウィンドウの場合は、座標は親ウィンドウのクライアント領域を基準とは。 ウィンドウがトップレベル ウィンドウの場合は、座標は、画面を基準とは。

*lppos*<br/>
指す、 [WINDOWPOS](../../mfc/reference/windowpos-structure1.md)ウィンドウを移動またはサイズ変更の原因となった操作で指定されたサイズと位置の値を含む構造体。

## <a name="requirements"></a>要件

**ヘッダー:** winuser.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

