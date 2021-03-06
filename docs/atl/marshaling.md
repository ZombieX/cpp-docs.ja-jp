---
title: マーシャ リング |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69f1b7e131b614aa4714f0c2be19fab79982031c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108626"
---
# <a name="marshaling"></a>マーシャ リング

マーシャ リングの COM の手法は、別のプロセスで使用する 1 つのプロセス内のオブジェクトによって公開されるインターフェイスを使用できます。 マーシャ リングすると、COM コードを提供します (またはインターフェイスの実装者によって提供されるコードを使用) をプロセス間で (および、他のコンピューターで実行されているプロセスをネットワーク経由で) に移動できる形式にメソッドのパラメーターをパックして、これらのパラメーターをアンパックするのにはもう一方の end。 同様に、COM では、呼び出しから返された場合は、同様の手順を実行する必要があります。

> [!NOTE]
>  マーシャ リングは通常必要ありませんオブジェクトによって提供されるインターフェイスは、オブジェクトと同じプロセスで使用されている場合です。 ただし、スレッド間マーシャ リングを必要に可能性があります。

## <a name="see-also"></a>関連項目

[COM の概要](../atl/introduction-to-com.md)<br/>
[マーシャ リングの詳細](/windows/desktop/com/marshaling-details)

