---
title: プロジェクトにフォームの挿入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba22c87ee601d66ccfb1092047e69be42d8163c3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052755"
---
# <a name="inserting-a-form-into-a-project"></a>プロジェクトへのフォームの挿入

フォームは、コントロールの便利なコンテナーを提供します。 簡単に、アプリケーションが MFC ライブラリをサポートしていれば、MFC ベースのフォームをアプリケーションに挿入できます。

### <a name="to-insert-a-form-into-your-project"></a>プロジェクトにフォームを挿入するには

1. クラス ビュー、フォームを追加するプロジェクトを選択し、マウスの右ボタンをクリックします。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**クラスの追加**します。

   場合、**新しいフォーム**コマンドは使用できません、プロジェクトは、Active Template Library (ATL) に基づく可能性があります。 ATL プロジェクトには、フォームを追加するにする必要があります[特定の設定を指定](../atl/reference/application-settings-atl-project-wizard.md)プロジェクトを作成しているとき。

1. **MFC**フォルダー、をクリックして**MFC クラス**します。

1. 派生する新しいクラスを MFC クラス ウィザードを使用する[CFormView](../mfc/reference/cformview-class.md)します。

Visual C から開始できるように、ダイアログ エディター内で開くアプリケーションには、フォームが追加コントロールを追加し、その全体的な設計に取り組んでいます。

(この機能は、ダイアログ ベースのアプリケーションには適用されません)、次の手順を実行する可能性があります。

1. 上書き、`OnUpdate`メンバー関数。

1. ビューからデータをドキュメントに移動するメンバー関数を実装します。

1. 作成、`OnPrint`メンバー関数。

## <a name="see-also"></a>関連項目

[フォーム ビュー](../mfc/form-views-mfc.md)

