---
title: ABC 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4f0367e19589093b31fcd64d5312e7b47e8a043
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080274"
---
# <a name="abc-structure"></a>ABC 構造体

`ABC`構造には、TrueType フォントの文字の幅が含まれています。

## <a name="syntax"></a>構文

```
typedef struct _ABC { /* abc */
    int abcA;
    UINT abcB;
    int abcC;
} ABC;
```

#### <a name="parameters"></a>パラメーター

*abcA*<br/>
文字の A の間隔を指定します。 A の間隔は、文字のグリフを描画する前に、現在の位置に追加する距離です。

*abcB*<br/>
文字の B の間隔を指定します。 B の間隔は、文字のグリフの描画の部分の幅です。

*abcC*<br/>
C の文字の間隔を指定します。 C の間隔は、文字のグリフの右側に空白文字を提供する現在の位置に追加する距離です。

## <a name="remarks"></a>Remarks

文字の幅の合計は、A、B、および C のスペースの合計です。 A または C 領域のいずれかをスペーシングまたはオーバー ハングを示す負にすることができます。

## <a name="requirements"></a>必要条件

**ヘッダー:** wingdi.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

