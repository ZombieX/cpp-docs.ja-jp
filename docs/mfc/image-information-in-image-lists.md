---
title: イメージのイメージ リストの情報 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98bc629cde74cf7a6fc8a416de862f50a1dd5ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422286"
---
# <a name="image-information-in-image-lists"></a>イメージ リストのイメージ情報

[CImageList](../mfc/reference/cimagelist-class.md)多数イメージの一覧から情報を取得する関数にはが含まれています。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)メンバー関数、`IMAGEINFO`イメージとマスク ビットマップのカラー プレーンと、ピクセルあたりのビット数、および外接する四角形のハンドルを含む、1 つのイメージに関する情報を含む構造体イメージ、ビットマップ内のイメージです。 この情報を使用すると、イメージのビットマップを直接操作します。

[GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)メンバー関数は、イメージ リスト内のイメージの数を取得します。

使用して、イメージとイメージ リスト内のマスクに基づいてアイコンを作成することができます、 [extracticon 関数](../mfc/reference/cimagelist-class.md#extracticon)メンバー関数。 関数は、新しいアイコンのハンドルを返します。

## <a name="see-also"></a>関連項目

[CImageList の使い方](../mfc/using-cimagelist.md)<br/>
[コントロール](../mfc/controls-mfc.md)

