---
title: ATL レジストリ コンポーネント (レジストラー) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- registry, accessing
- ATL Registrar
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: 106752ae-4cfc-4030-8cb2-d36a1d635a2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d3f8f52e237fe364f73057c81eb17c8fd3def18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041039"
---
# <a name="atl-registry-component-registrar"></a>ATL レジストリ コンポーネント (レジストラー)

ATL レジストラーでは、カスタム インターフェイス経由でシステムのレジストリに最適化されたアクセスを提供します。 レジストラーは、フリー スレッドし、C++ のクライアントのコードの静的にリンクできます。

> [!NOTE]
>  ATL レジストラーのソース コードは、atlmfc\include\atliface.h で確認できます。

## <a name="in-this-section"></a>このセクションの内容

[レジストラー スクリプトの作成](../atl/creating-registrar-scripts.md)<br/>
レジストラー スクリプトを作成するためのガイド。 BNF 構文、解析ツリー、レジストリのスクリプトの例については、置き換え可能パラメーターを使用して、スクリプトの呼び出しについてのトピックが含まれています。

[レジストラー コード (C++ のみ) に静的にリンクの設定](../atl/setting-up-a-static-link-to-the-registrar-code-cpp-only.md)<br/>
レジストラーに静的にリンクを設定する手順について説明します。

## <a name="related-sections"></a>関連項目

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Active Template Library を使用してプログラミングする方法に関する概念説明のトピックへのリンクを提供します。

