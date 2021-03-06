---
title: プロパティ ページ (ATL チュートリアル、パート 6) の追加 |Microsoft Docs
ms.custom: get-started-article
ms.date: 09/27/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00390f5a5872c183fdea385158dfa5020362a06f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055064"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>プロパティ ページの追加 (ATL チュートリアル、パート 6)

プロパティ ページは、必要な場合に共有することを許可する個別の COM オブジェクトとして実装されます。 この手順では、コントロールにプロパティ ページを追加するタスクを次の操作を行います。

- プロパティ ページのリソースの作成

- 作成して、プロパティ ページを管理するコードを追加します。

- コントロールのプロパティ ページの追加

## <a name="creating-the-property-page-resource"></a>プロパティ ページのリソースの作成

コントロールにプロパティ ページを追加するには、ATL プロパティ ページのテンプレートを使用します。

### <a name="to-add-a-property-page"></a>プロパティ ページを追加するには

1. **ソリューション エクスプ ローラー**、右クリックして`Polygon`します。

1. ショートカット メニューで、**追加** > **新しい項目の**します。

1. テンプレートの一覧から選択**ATL** > **ATL プロパティ ページ**クリック**追加**します。

1. ときに、 **ATL プロパティ ページ ウィザード**が表示されたら、入力*PolyProp*として、**短い**名。

1. をクリックして**文字列**を開く、**文字列**ページし、入力 **& 多角形**として、**タイトル**。

   **タイトル**プロパティのページには、そのページのタブに表示される文字列。 **ドキュメント文字列**プロパティ フレームを使用してステータス行またはツール ヒントに表示される説明です。 いる標準プロパティ フレーム現在を使用しない、この文字列のため既定の内容のままにすることができますに注意してください。 生成されません、**ヘルプ ファイル**現時点では、そのテキスト ボックス内のエントリをので削除します。

1. クリックして**完了**、プロパティ ページのオブジェクトが作成されます。

次の 3 つのファイルが作成されます。

|ファイル|説明|
|----------|-----------------|
|PolyProp.h|C++ クラスを含む`CPolyProp`、プロパティ ページを実装します。|
|PolyProp.cpp|PolyProp.h ファイルが含まれています。|
|Polyprop.rgs という|プロパティ ページ オブジェクトを登録、レジストリ スクリプト。|

次のコードの変更も作成されます。

- Polygon.cpp のオブジェクトのエントリのマップに新しいプロパティ ページが追加されます。

- `PolyProp`クラス Polygon.idl ファイルに追加されます。

- 新しい polyprop.rgs というレジストリ スクリプト ファイルは、プロジェクトのリソースに追加されます。

- ダイアログ ボックスのテンプレートは、プロパティ ページのプロジェクトのリソースに追加されます。

- 指定したプロパティの文字列は、リソース文字列テーブルに追加されます。

プロパティ ページに表示するフィールドを追加します。

### <a name="to-add-fields-to-the-property-page"></a>プロパティ ページにフィールドを追加するには

1. **ソリューション エクスプ ローラー**、Polygon.rc リソース ファイルをダブルクリックします。 これが開きます**リソース ビュー**します。

1. **リソース ビュー**、展開、`Dialog`ノードをダブルクリックします`IDD_POLYPROP`します。 表示されるダイアログ ボックスがここにコントロールを挿入するかを示すラベルを除く空であることに注意してください。

1. そのラベルを選択し、変更を読み取る`Sides:`変更することによって、**キャプション**内のテキスト、**プロパティ**ウィンドウ。

1. [ラベル] ボックスのサイズを変更して、テキストのサイズが収まるようにします。

1. ドラッグ、**エディット コントロール**から、**ツールボックス**ラベルの右側にします。

1. 最後に、変更、 **ID**するエディット コントロールの`IDC_SIDES`を使用して、**プロパティ**ウィンドウ。

これは、プロパティ ページのリソースを作成するプロセスを完了します。

## <a name="adding-code-to-create-and-manage-the-property-page"></a>作成して、プロパティ ページを管理するコードを追加します。

プロパティ ページのリソースを作成する実装コードを記述する必要があります。

まず、有効にする、`CPolyProp`クラス、オブジェクトに、辺の数を設定するときに、**適用**ボタンが押されました。

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>辺の数を設定する適用関数を変更するには

1. 置換、 `Apply` PolyProp.h で次のコードの関数。

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

プロパティ ページが接続して、一度に 1 つ以上のクライアントがあることができますので、`Apply`関数はループに呼び出す`put_Sides`エディット ボックスから取得した値を持つ各クライアントでします。 使用している、 [CComQIPtr](../atl/reference/ccomqiptr-class.md)クラスは、実行、`QueryInterface`を取得するには、各オブジェクトに対して、`IPolyCtl`からインターフェイス、`IUnknown`インターフェイス (に格納されている、`m_ppUnk`配列)。

コードでは、その設定をチェック、`Sides`プロパティが実際に機能します。 コードがからエラーの詳細を表示するメッセージ ボックスを表示して失敗した場合、`IErrorInfo`インターフェイス。 コンテナーのためのオブジェクトが、通常、`ISupportErrorInfo`インターフェイスと呼び出し`InterfaceSupportsErrorInfo`最初は、オブジェクトがエラー情報の設定をサポートするかどうかを確認します。 このタスクをスキップすることができます。

[CComPtr](../atl/reference/ccomptr-class.md)を呼び出す必要はありませんので、参照カウントを自動的に処理することで役立つ`Release`インターフェイス。 `CComBSTR` 最後に実行する必要はありませんので、BSTR の処理では、`SysFreeString`呼び出します。 使用することも、さまざまな文字列変換クラスのいずれか (これは、関数の先頭を理由) 必要に応じて、BSTR を変換できるようにします。

いることを示すプロパティ ページのダーティー フラグを設定する必要があります、**適用**ボタンが有効にする必要があります。 これは、ユーザーの値が変更されたときに発生します。、**辺**編集ボックス。

### <a name="to-handle-the-apply-button"></a>[適用] ボタンを処理するには

1. **クラス ビュー**、右クリックして`CPolyProp`] をクリック**プロパティ**ショートカット メニューの [します。

1. **プロパティ**ウィンドウで、をクリックして、**イベント**アイコン。

1. 展開、`IDC_SIDES`ノードは、イベントの一覧表示します。

1. 選択`EN_CHANGE`、右側のドロップダウン メニューから次のようにクリックします。 **\<追加 > OnEnChangeSides**します。 `OnEnChangeSides`ハンドラーの宣言は、Polyprop.h と Polyprop.cpp するハンドラーの実装に追加されます。

次に、ハンドラーを変更します。

### <a name="to-modify-the-onenchangesides-method"></a>OnEnChangeSides メソッドを変更するには

1. 次のコードを追加する Polyprop.cpp で、`OnEnChangeSides`メソッド (ウィザードがそこに配置するすべてのコードを削除する)。

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` 呼び出されるときに、`WM_COMMAND`でメッセージが送信される、`EN_CHANGE`の通知、`IDC_SIDES`コントロール。 `OnEnChangeSides` 呼び出して`SetDirty`プロパティ ページがダーティようになりましたことを示す TRUE を渡すと、**適用**ボタンが有効にする必要があります。

## <a name="adding-the-property-page-to-the-control"></a>コントロールのプロパティ ページの追加

ATL プロパティ ページのテンプレートおよびウィザードに対する追加しないでプロパティ ページをコントロールにする、自動的にプロジェクトでを複数のコントロールにある可能性があるため。 コントロールのプロパティのマップにエントリを追加する必要があります。

### <a name="to-add-the-property-page"></a>プロパティ ページを追加するには

1. PolyCtl.h を開き、プロパティ マップに次の行を追加します。

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

コントロールのプロパティのマップは、次のようになります。

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

追加する可能性があります、`PROP_PAGE`マクロを使用する場合は、プロパティ ページの CLSID、`PROP_ENTRY`マクロに示すように、`Sides`プロパティの値は、コントロールを保存するときにも保存します。

マクロに 3 つのパラメーターは、プロパティの DISPID とをプロパティを持つプロパティ ページの CLSID は、プロパティの説明です。 これなど、Visual Basic にコントロールを読み込むし、デザイン時に、辺の数を設定した場合に便利です。 辺の数を保存すると、Visual Basic プロジェクトを再読み込みするときに、ため、辺の数が復元されます。

## <a name="building-and-testing-the-control"></a>コントロールのビルドとテスト

コントロールをビルドし、ActiveX コントロール テスト コンテナーに挿入するようになりました。 **テスト コンテナー**の**編集** メニューのをクリックして**PolyCtl クラス オブジェクト**します。 プロパティ ページは、追加した情報が表示されます。

**適用**ボタンが最初に無効になります。 値の入力を開始、**辺**ボックスおよび**適用**ボタンが有効になります。 値を入力したら、クリックして、**適用**ボタンをクリックします。 コントロールの表示の変更、および**適用**ボタンが再び無効になります。 無効な値を入力してください。 エラーの説明から設定を含むメッセージ ボックスが表示されます、`put_Sides`関数。

次に、Web ページ上にコントロールを格納します。

[手順 5 に戻る](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [手順 7 に](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>関連項目

[チュートリアル](../atl/active-template-library-atl-tutorial.md)
