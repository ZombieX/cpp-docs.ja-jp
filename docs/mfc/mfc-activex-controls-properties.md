---
title: 'MFC ActiveX コントロール: プロパティ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27cdbd548366bcf02e2d6282b309402cf25af2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401616"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX コントロール : プロパティ

ActiveX コントロールは、そのコントロールのコンテナーとの通信にイベントを発生させます。 コンテナーでは、コントロールと通信するメソッドとプロパティを代わりに、使用します。 メソッドとプロパティは使用し、目的のようなそれぞれ、メンバー関数と C++ のクラスのメンバー変数にです。 プロパティは、任意のコンテナーに公開されている ActiveX コントロールのデータ メンバーです。 プロパティは、オートメーション クライアントや ActiveX コントロール コンテナーなどの ActiveX コントロールを含むアプリケーションのインターフェイスを提供します。

プロパティは、属性とも呼ばれます。

ActiveX コントロールのメソッドの詳細については、記事を参照してください。 [MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)します。

ActiveX コントロールには、在庫とカスタム メソッドとプロパティの両方を実装できます。 クラス`COleControl`ストック プロパティの実装を提供します。 (ストック プロパティの完全な一覧は、記事を参照してください[MFC ActiveX コントロール: ストック プロパティの追加](../mfc/mfc-activex-controls-adding-stock-properties.md)。)。開発者は、によって定義されたカスタムのプロパティは、ActiveX コントロールに特別な機能を追加します。 詳細については、次を参照してください。 [MFC ActiveX コントロール: カスタム プロパティを追加する](../mfc/mfc-activex-controls-adding-custom-properties.md)します。

メソッドと同様に、カスタムおよびストックの両方のプロパティがプロパティおよびメソッドとの既存のメンバー関数を処理するディスパッチ マップで構成されるメカニズムによってサポートされている、`COleControl`クラス。 さらに、これらのプロパティは、開発者がコントロールに追加情報を渡すために使用するパラメーターを持つことができます。

次の記事では、さらに詳しく ActiveX コントロールのプロパティについて説明します。

- [MFC ActiveX コントロール: ストック プロパティの追加](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [MFC ActiveX コントロール: カスタム プロパティの追加](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [MFC ActiveX コントロール: 高度なプロパティの実装](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [MFC ActiveX コントロール: アンビエント プロパティへのアクセス](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)

