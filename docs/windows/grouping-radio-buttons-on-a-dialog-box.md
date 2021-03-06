---
title: ダイアログ ボックス (C++) のオプション ボタンをグループ化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5615756f8716ae1f4c73ccf98e2754b57f674216
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392965"
---
# <a name="grouping-radio-buttons-on-a-dialog-box-c"></a>オプション ボタンをグループ化 ダイアログ ボックス (C++)

ダイアログ ボックスにラジオ ボタンを追加するときに扱うグループとして設定して、**グループ**プロパティ、**プロパティ**グループ内の最初のボタンのウィンドウ。 そのラジオ ボタンのコントロール ID が [メンバー変数の追加ウィザード](../ide/add-member-variable-wizard.md)に表示され、ラジオ ボタンのグループのメンバー変数を追加できるようになります。

1 つのダイアログ ボックスにラジオ ボタンの複数のグループを設定できます。各グループは次の手順を使用して追加する必要があります。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>ラジオ ボタンのグループをダイアログ ボックスに追加するには

1. [[ツールボックス] ウィンドウ](/visualstudio/ide/reference/toolbox) でラジオ ボタン コントロールを選び、ダイアログ ボックス内でそのコントロールを配置する位置をクリックします。

2. 手順 1.を繰り返して、必要な数のラジオ ボタンを追加します。 グループのラジオ ボタンがタブ オーダーで連続していることを確認します (詳しくは「 [コントロールのタブ オーダーの変更](../windows/changing-the-tab-order-of-controls.md)」をご覧ください)。

3. [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で、タブ オーダーが **最初** のラジオ ボタンの *[グループ]* プロパティを **[True]** に設定します。

   **[グループ]** プロパティを **[True]** に変更すると、リソース スクリプトのダイアログ オブジェクト内でそのボタンのエントリに WS_GROUP スタイルが追加されます。このため、ユーザーはボタン グループのラジオ ボタンを一度に 1 つしか選べなくなります (ユーザーがラジオ ボタンを 1 つクリックすると、グループの残りのボタンはクリアされます)。

   > [!NOTE]
   > **[グループ]** プロパティを **[True]** に設定する必要があるのは、グループ内の最初のラジオ ボタンだけです。 ボタン グループに属さないその他のコントロールがある場合は、 **グループ以外の** 最初のコントロールの *[グループ]* プロパティも同様に **[True]** に設定します。 キーを押して、グループ外の最初のコントロールをすばやく識別できます**Ctrl**+**D**タブ オーダーを表示します。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>ラジオ ボタン グループのメンバー変数を追加するには

1. タブ オーダーの最初のラジオ ボタン コントロール (主要なコントロールであり、 **[グループ]** プロパティが [True] に設定されている) を右クリックします。

2. ショートカット メニューの **[変数の追加]** を選びます。

3. [[メンバー変数の追加ウィザード]](../ide/add-member-variable-wizard.md)で、 **[コントロール変数]** チェック ボックスをオンにして、次に **[値]** ラジオ ボタンを選びます。

4. **[変数名]** ボックスに、新しいメンバー変数の名前を入力します。

5. **変数の型**リスト ボックスで、 **int**または型`int`します。

6. これで、コードを変更し、表示したときに選ばれているラジオ ボタンを指定できます。 たとえば、`m_radioBox1 = 0;`グループ内の最初のラジオ ボタンを選択します。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>要件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロールの配置](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[コントロール](../mfc/controls-mfc.md)