---
title: ATL COM プロパティ ページ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 208c89cad441a1fae70f5532204ec7856459de7f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095860"
---
# <a name="atl-com-property-pages"></a>ATL COM プロパティ ページ

プロパティを設定するためのユーザー インターフェイスを提供する COM プロパティ ページ (またはメソッドの呼び出し) の 1 つまたは複数の COM オブジェクト。 プロパティ ページが、デザイン時に設定するコントロールのプロパティをできる機能豊富なユーザー インターフェイスを提供するための ActiveX コントロールで広範囲に使用されます。

プロパティ ページは、COM オブジェクトを実装する、 [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)または[IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2)インターフェイス。 これらのインターフェイスに関連付けられているページをできるようにするメソッドを提供する、 `site` (ページのコンテナーを表す COM オブジェクト) の数と*オブジェクト*変更に応じてそのメソッドが呼び出されます (COM オブジェクトユーザーが行ったプロパティ ページの)。 プロパティ ページのコンテナーは、またはそのユーザー インターフェイスと、変更を適用する場合に非表示には、基になるオブジェクトをユーザーが行った場合に、ページに通知するプロパティ ページのインターフェイスのメソッドを呼び出して責任を負います。

オブジェクトのプロパティを設定するとは無関係に、各プロパティ ページを完全に構築できます。 いるプロパティ ページが必要なを特定のインターフェイス (または一連のインターフェイス) を理解し、そのインターフェイスのメソッドを呼び出すためのユーザー インターフェイスを提供します。

詳細については、次を参照してください。[プロパティ シートとプロパティ ページ](/windows/desktop/com/property-sheets-and-property-pages)Windows SDK に含まれています。

## <a name="in-this-section"></a>このセクションの内容

[プロパティ ページの指定](../atl/specifying-property-pages.md)<br/>
コントロールのプロパティ ページを指定するための手順と、クラスの例を示します。

[プロパティ ページの実装](../atl/implementing-property-pages.md)<br/>
オーバーライドするメソッドを含めて、プロパティ ページを実装するための手順を一覧表示します。 ATLPages サンプル プログラムに基づく完全な例を示します。

## <a name="related-sections"></a>関連項目

[例](../visual-cpp-samples.md)<br/>
使用してプロパティ ページを実装する例のサンプルの要約`IPropertyPageImpl`します。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Active Template Library を使用してプログラミングする方法に関する概念説明のトピックへのリンクを提供します。

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)

