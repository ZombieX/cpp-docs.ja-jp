---
title: MDI タブ付きグループ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35113181a21a5ff265b12269f57ee853f6011abc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442163"
---
# <a name="mdi-tabbed-groups"></a>MDI タブ付きグループ

マルチ ドキュメント インターフェイス (MDI) のタブ付きグループ機能により、1 つまたは複数のタブ付きウィンドウを表示する、マルチ ドキュメント インターフェイス (MDI) アプリケーション (またはグループと呼ばれる、タブ付きウィンドウの*タブ付きグループ*) MDI クライアント領域にします。 タブ付きウィンドウは、垂直方向または水平方向に配置できます。 アプリケーションでは、1 つ以上の MDI タブ付きグループをホストしている場合、グループは、スプリッターで区切られます。

## <a name="features"></a>フィーチャー

MDI タブ付きグループの機能は、次のとおりです。

- アプリケーションでは、タブ付きウィンドウを動的に作成できます。

- アプリケーションは、水平方向または垂直方向にタブ付きウィンドウを整列できます。

- タブ付きウィンドウのグループは、スプリッターで区切られます。 ユーザーは、スプリッターを使用してタブ付きグループのサイズを変更できます。

- ユーザーは、グループ間で、個々 のタブをドラッグできます。

- ユーザーは、新しいグループを作成する個々 のタブをドラッグできます。

- ユーザーでは、タブを移動したり、ショートカット メニューを使用して新しいグループを作成することができます。

- アプリケーションは、保存して、タブ付きウィンドウのレイアウトを読み込むことができます。

- アプリケーションは、保存し、MDI ドキュメントの一覧を読み込むことができます。

- アプリケーションでは、個々 のタブ付きグループにアクセスでき、そのパラメーターを変更することができます。

### <a name="using-mdi-tabbed-groups"></a>MDI を使用してタブ付きグループ

以下は、通常は MDI タブ付きグループで実行されるタスクです。

- メイン フレーム ウィンドウの MDI タブ付きグループを有効にするのには、呼び出す[cmdiframewndex::enablemditabbedgroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)します。 このメソッドの 2 番目のパラメーターのインスタンスである、`CMDITabInfo`クラス。 既定のパラメーターを使用または呼び出す前にそれらを変更できます`CMDIFrameWndEx::EnableMDITabbedGroups`します。

- 実行時に MDI タブ付きグループのプロパティを変更するには、作成または変更、`CMDITabInfo`オブジェクトと呼び出し`CMDIFrameWndEx::EnableMDITabbedGroups`もう一度

- タブ付きウィンドウの MDI の一覧を取得する、呼び出す`CMDIFrameWndEx::GetMDITabGroups`します。

- 作業中のタブ付きグループの横にある新しい MDI タブ付きグループを作成するには`CMDIFrameWndEx::MDITabNewGroup`します。

- タブ付きグループの前または次のウィンドウに入力フォーカスをシフトする呼び出す`CMDIFrameWndEx::MDITabMoveToNextGroup`します。

- タブ付きグループの呼び出しをウィンドウ、MDI のメンバーであるかどうかを判断する`CMDIFrameWndEx::IsMemberOfMDITabGroup`します。

- メイン フレーム ウィンドウの MDI タブまたは MDI タブ付きグループが有効になっているかどうかを確認するのには、呼び出す`CMDIFrameWndEx::AreMDITabs`します。 MDI タブ付きグループが有効になっているかどうかにのみを確認を呼び出す`CMDIFrameWndEx::IsMDITabbedGroup`します。

- ユーザーがタブをクリックしてまたは別の MDI タブ付きグループにドラッグしたときにショートカット メニューを表示するには、オーバーライド`CMDIFrameWndEx::OnShowMDITabContextMenu`で、 `CMDIFrameWndEx`-クラスを派生します。 このメソッドを実装していない場合でも、アプリケーションでは、ショートカット メニューは表示されません。

- アプリケーションで MDI タブ付きグループのレイアウトを保存する`CMDIFrameWndEx::SaveMDIState`します。 タブ付きグループのプロファイルを以前に保存した MDI を読み込むには、`CMDIFrameWndEx::LoadMDIState`します。 読み込みまたは MDI アプリケーションで開かれたドキュメントの一覧を保存するこれらのメソッドを呼び出すこともできます。 保存と読み込みの状態の MDI の詳細については、次を参照してください。 [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate)します。

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス要素](../mfc/user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx クラス](../mfc/reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx クラス](../mfc/reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo クラス](../mfc/reference/cmditabinfo-class.md)
