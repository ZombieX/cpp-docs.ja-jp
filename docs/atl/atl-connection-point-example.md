---
title: ATL 接続ポイントの例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9aafd2676b1816737015b6af4fdbc9b3a710ae5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752359"
---
# <a name="atl-connection-point-example"></a>ATL 接続ポイントの例

この例は、サポートするオブジェクトを示しています。 [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)アウトゴーイング インターフェイスとして。

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

指定するときに`IPropertyNotifySink`クラスを使用する送信インターフェイスとして[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)の代わりに`IConnectionPointImpl`します。 例えば:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>関連項目

[接続ポイント](../atl/atl-connection-points.md)

