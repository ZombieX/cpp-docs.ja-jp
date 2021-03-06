---
title: MFC ActiveX コントロール コンテナーの作成 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.container
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37119934a70f8a68d32ed83699fa6deb012d8879
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404437"
---
# <a name="creating-an-mfc-activex-control-container"></a>MFC ActiveX コントロール コンテナーの作成

ActiveX コントロール コンテナーは、実行する (旧 OLE) の ActiveX コントロール用の環境を提供する親プログラムです。 対応の有無にかかわらず、MFC ActiveX コントロールを含むアプリケーションを作成することができますより簡単に MFC を行います。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の上書きの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](../activex-controls.md)します。

MFC プログラムを使用してコンテナーを作成、 [MFC アプリケーション ウィザード](../../mfc/reference/mfc-application-wizard.md)MFC と ActiveX クラスによって実装されている ActiveX コントロールと自動化の多くの機能にアクセスすることができます。 これらの機能は、ビジュアル編集、自動化、複合ファイルを作成して、コントロールのサポートします。 親プログラムをサポートする MFC アプリケーション ウィザードのビジュアル編集オプションには、コンテナー、ミニ サーバー、フル サーバー、およびコンテナーとサーバーの両方のプログラムの作成が含まれます。

- **新しい MFC アプリケーション**します。 オートメーションを含む新しい MFC プログラムを作成するには、ビジュアル編集、複合ファイル、またはコントロールのサポート、MFC アプリケーション ウィザードを使用してを適切なオートメーション オプションを選択します。

- **既存の MFC アプリケーション**します。 コントロール コンテインメントを既存の MFC アプリケーションに追加する場合は、次を参照してください。 [OLE コントロール コンテナー: OLE コントロール コンテインメントの手動で有効にする](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)します。

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>アプリケーションの種類は次のいずれかの ActiveX コンテナーを作成するには

1. [コンテナー](../../mfc/containers.md)

1. [ビジュアル編集](../../mfc/ole-mfc.md)

1. [MFC ActiveX コントロールします。](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>関連項目

[Visual C++ プロジェクトの種類](../../ide/visual-cpp-project-types.md)

