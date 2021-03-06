---
title: MFC クラス ウィザード |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.wizards.classwizard
dev_langs:
- C++
helpviewer_keywords:
- wizards (MFC)
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31e8b6064b9e81edac1c7f4c8aac8e20f1f72296
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438458"
---
# <a name="mfc-class-wizard"></a>MFC クラス ウィザード

プロジェクト内のクラスにメッセージおよびメッセージ ハンドラーを追加できます。 他のウィザードを起動したり、プロジェクトにクラスを追加したりすることもできます。

開くには、 **MFC クラス ウィザード**の**プロジェクト** メニューのをクリックして**クラス ウィザード**します。 キーボード ショートカットでこのウィザードを開く場合は、Ctrl キーと Shift キーを押しながら X キーを押します。

## <a name="uielement-list"></a>UIElement の一覧

- **プロジェクト**

   ソリューション内のプロジェクトの名前。

   ドロップダウン リスト ボックスで、ソリューションの他のプロジェクトを選択できます。

- **クラス名**

   プロジェクト内のクラスの名前。

   内のクラスを選択すると、**クラス名** ボックスの一覧でコントロールを設定するクラスからのデータ、 **MFC クラス ウィザード**します。 コントロールの値を変更すると、選択したクラスのデータに変更が反映されます。

- **クラスを追加します。**

   いくつかのソースの 1 つからクラスを追加できます。

   選択内容に応じて、 **MFC クラス追加ウィザード**、 **Typelib クラス追加ウィザード**、**クラスの追加から ActiveX コントロール ウィザード**、または**MFC ODBCコンシューマー ウィザード**が開始します。

- **基本クラス**

   表示されるクラスの基底クラス**クラス名**します。

- **クラス宣言**

   クラスを**クラス名**クラスを宣言します。

   **クラス宣言**が名前で名前と異なる場合にのみボックスが表示されます**クラスの実装**します。

- **リソース**

   内のリソースの ID**クラス名**、存在する場合。 それ以外の場合、**リソース**ボックスが空です。

- **クラスの実装**

   内のクラスの実装を格納するファイルの名前**クラス名**します。

   矢印をクリックすることで、別の実装ファイルを選択できます。 利用可能なオプションの一覧を次の表に示します。

   |オプション|説明|
   |------------|-----------------|
   |**ファイルを開く**|クラス ウィザードを終了し、現在のクラスの実装ファイルを開きます。|
   |**フォルダーを開く**|現在のクラス実装ファイルのあるフォルダーを開きます。|
   |**完全なパスをクリップボードにコピーします。**|現在の実装ファイルのパスをクリップボードにコピーします。|

- **[コマンド]**

   コマンドとそのメッセージ ハンドラーを追加、削除、編集、または検索できます。

   ハンドラーを追加するには、次のようにクリックします。**ハンドラーの追加**、内の項目をダブルクリックします。 または、**オブジェクト Id**一覧または**メッセージ**一覧。 結果として得られる関数の名前、ID、およびメッセージが表示されます、**メンバー関数**一覧。

   ハンドラーを削除するには、内の項目を選択、**メンバー関数**ボックスの一覧をクリックして**削除ハンドラー**します。

   ハンドラーを変更するに対応する項目をダブルクリック、**メンバー関数**一覧。 または、リスト ボックスで項目を選択し、**コードの編集**します。

- **メッセージ**

   メッセージとそのメッセージ ハンドラーを追加、削除、編集、または検索できます。

   ハンドラーを追加するには、次のようにクリックします。**ハンドラーの追加**、内の項目をダブルクリックします。 または、**メッセージ**一覧。

   カスタム メッセージを追加するには、次のようにクリックします。**カスタム メッセージの追加**または Enter キーを押すと、で値を指定します、**カスタム メッセージの追加** ダイアログ ボックス。 そのダイアログ ボックスで選択することも**登録メッセージ**オペレーティング システム全体で一意であることが保証されるウィンドウ メッセージを処理します。

- **仮想関数**

   仮想関数またはオーバーライドされた仮想関数を追加、削除、編集、または検索できます。

- **メンバー変数**

   メンバー変数を追加、削除、編集、または検索できます。

- **メソッド**

   メソッドを追加、削除、または検索したり、メソッドの定義または宣言に移動したりできます。

   メソッドを追加するには、次のようにクリックします。**メソッドの追加**、次の値を指定し、**メソッドの追加** ダイアログ ボックス。

   メソッドを削除するには、内の項目を選択、**メソッド**を一覧表示し、 **Delete メソッド**します。

   宣言を表示するには、内の項目を選択、**メソッド**を一覧表示し、**宣言に移動します。**

   定義を表示するには、内の項目をダブルクリックします。、**メソッド**一覧。 または、内の項目を選択、**メソッド**ボックスの一覧をクリックして、**定義へ移動**ボタンをクリックします。

## <a name="see-also"></a>関連項目

[クラスの追加](../../ide/adding-a-class-visual-cpp.md)
