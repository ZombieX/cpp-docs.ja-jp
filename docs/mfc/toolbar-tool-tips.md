---
title: ツールバーのツール ヒント |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23ab29a219899f2c40e1b5c4a458d35f97cf49a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434415"
---
# <a name="toolbar-tool-tips"></a>ツール バーのツール ヒント

ツール ヒントは、一定期間、ボタンの上でマウスを配置するときに、ツール バー ボタンの目的の簡単な説明を表示する小さなポップアップ ウィンドウです。 アプリケーション ウィザードは、ツールバーがありますアプリケーションを作成するときにツール ヒントのサポートが提供されます。 この記事では、アプリケーションのウィザードとツール ヒントのサポートをアプリケーションに追加する方法によって作成された、両方のツール ヒント サポートについて説明します。

この記事では次の内容について説明します。

- [ツール ヒントをアクティブ化します。](#_core_activating_tool_tips)

- [ステータス バーのフライ バイ更新](#_core_fly_by_status_bar_updates)

##  <a name="_core_activating_tool_tips"></a> ツール ヒントをアクティブ化します。

アプリケーションでのツール ヒントを有効にするには、2 つの処理を行う必要があります。

- その他のスタイルに CBRS_TOOLTIPS スタイルを追加 (WS_CHILD、WS_VISIBLE、およびその他など**cbrs _** スタイル) として渡される、 *dwStyle*パラメーターを[用意されて](../mfc/reference/ctoolbar-class.md#create)関数または[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)します。

- 次の手順のように、ツールバーのコマンドのコマンド ライン プロンプトを含む文字列リソースを改行文字 ('\n') で区切られた、ツールバーのヒント テキストを追加します。 文字列リソースは、ツールバーのボタンの ID を共有します。

#### <a name="to-add-the-tool-tip-text"></a>ツール ヒントのテキストを追加するには

1. ツール バー エディターのツールバーを編集するときに開く、**ツール バー ボタン プロパティ**指定したボタンのウィンドウ。

1. **プロンプト**ボックスで、そのボタンのツールヒントに表示するテキストを指定します。

> [!NOTE]
>  ツールバー エディターでボタン プロパティには、これまでの手順では、する必要があるが置き換えられますとテキストの設定を開くし、文字列リソースを編集します。

ツール ヒントが有効になっているコントロール バーに配置される子コントロールがある場合は、コントロール バーは、次の条件を満たす限り、そのコントロール バー上のすべての子コントロールのツールヒントに表示されます。

- コントロールの ID が 1 ではないのです。

- リソース ファイル内の子コントロールと同じ ID を持つストリング テーブル エントリには、ツール ヒントの文字列があります。

##  <a name="_core_fly_by_status_bar_updates"></a> ステータス バーのフライ バイ更新

ツール ヒントに関連する機能は、「フライ バイ」ステータス バーの更新です。 既定では、ステータス バーにメッセージは、ボタンがアクティブになったときにのみ、特定のツールバーのボタンについて説明します。 渡されるスタイルの一覧に CBRS_FLYBY を含めることにより`CToolBar::Create`、マウス カーソルが実際には、ボタンをアクティブ化しないまま、ツールバー上に置いたときに更新されたこれらのメッセージがあることができます。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [MFC ツールバーの実装 (ツールバーに概要情報)](../mfc/mfc-toolbar-implementation.md)

- [ドッキングとフローティング ツールバー](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)と[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)クラス

- [ツール バー コントロールの操作](../mfc/working-with-the-toolbar-control.md)

- [古い形式のツールバーを使用します。](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>関連項目

[MFC ツール バーの実装](../mfc/mfc-toolbar-implementation.md)

