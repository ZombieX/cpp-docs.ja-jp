---
title: IDispatch と IErrorInfo のサポート |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d9c27dfe81c3bbd2978f418c8e942ac20190b30
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753609"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>IDispatch と IErrorInfo のサポート

テンプレート クラスを使用して[IDispatchImpl](../atl/reference/idispatchimpl-class.md)の既定の実装を提供する、`IDispatch Interface`オブジェクトの任意のデュアル インターフェイスの部分。

オブジェクトで使用する場合、`IErrorInfo`エラーは、クライアントにバックアップし、オブジェクトがサポートする必要がありますを報告するインターフェイス、`ISupportErrorInfo Interface`インターフェイス。 テンプレート クラスは、 [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)オブジェクトでエラーを生成する 1 つのインターフェイスしかない場合は、これを実装する簡単な方法を提供します。

## <a name="see-also"></a>関連項目

[ATL COM オブジェクトの基礎](../atl/fundamentals-of-atl-com-objects.md)

