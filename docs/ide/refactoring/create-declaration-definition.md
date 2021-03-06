---
title: 宣言/定義の作成 | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21edf09eb78d339c06c709b06e8fe43ea72475c4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808408"
---
# <a name="create-declaration--definition"></a>宣言/定義の作成
**機能:** 関数の宣言または定義をすぐに生成できます。

**条件:** 宣言を必要とする関数があるときか、関数を必要とする宣言があるとき。

**理由:** 宣言/定義は手動で作成できますが、この機能では自動で作成され、必要に応じて、ヘッダー/コード ファイルが作成されます。

**方法:**

1. 宣言または定義を作成する関数の上にテキストまたはマウス カーソルを置きます。

   ![強調表示されたコード](images/createdefinition_highlight.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、コンテキスト メニューから **[宣言/定義の作成]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、コンテキスト メニューから **[宣言/定義の作成]** を選択します。

1. 関数の宣言/定義がソースまたはヘッダー ファイルで作成されます。ポップアップ プレビュー ウィンドウで確認できます。  ソースまたはヘッダー ファイルが存在しない場合、それも作成され、プロジェクトに置かれます。

   ![宣言/定義の作成の結果](images/createdefinition_result.png)
