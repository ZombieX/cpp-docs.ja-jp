---
title: Active ドキュメント コンテナー |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f2d8dcc81a8e9843ffa84651a6404ba91c9ef3d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394253"
---
# <a name="active-document-containers"></a>Active ドキュメント コンテナー

Microsoft Office バインダーまたは Internet Explorer など、active ドキュメント コンテナーでは、異なるアプリケーションの種類を作成し、各アプリケーションの複数のフレームを使用して強制ではなく 1 つのフレーム内のいくつかのドキュメントを操作できます。ドキュメントの種類の場合)。

MFC での active ドキュメント コンテナーの完全なサポートを提供します、`COleDocObjectItem`クラス。 MFC アプリケーション ウィザードを使用して、選択して、active ドキュメント コンテナーを作成することができます、 **Active ドキュメント コンテナー**チェック ボックスをオン、**複合ドキュメント サポート**MFC アプリケーション ウィザードのページ。 詳細については、次を参照してください。 [Active ドキュメント コンテナー アプリケーションを作成する](../mfc/creating-an-active-document-container-application.md)します。

Active ドキュメント コンテナーの詳細についてを参照してください。

- [コンテナーの要件](#container_requirements)

- [サイト オブジェクトのドキュメント](#document_site_objects)

- [サイト オブジェクトの表示](#view_site_objects)

- [オブジェクトの構築](#frame_object)

- [[ヘルプ] メニューのマージ](../mfc/help-menu-merging.md)

- [プログラムによる印刷](../mfc/programmatic-printing.md)

- [コマンド ターゲット](../mfc/message-handling-and-command-targets.md)

##  <a name="container_requirements"></a> コンテナーの要件

Active ドキュメント コンテナーでのアクティブなドキュメントのサポートは、インターフェイスの実装だけを意味します。 含まれるオブジェクトのインターフェイスを使用しての知識も必要です。 同じでは、コンテナー、アクティブなドキュメント自体でそれらの拡張機能インターフェイスを使用する方法の理解をする必要がありますも、アクティブなドキュメントの拡張機能に適用されます。

Active ドキュメント コンテナー アクティブなドキュメントを統合する必要があります。

- オブジェクト ストレージを処理できる、`IPersistStorage`インターフェイス、つまり、提供する、`IStorage`アクティブな各ドキュメントのインスタンス。

- OLE ドキュメント「サイト」オブジェクト (ドキュメントまたは埋め込みごとに 1 つ) の基本的な埋め込み機能をサポートして実装する`IOleClientSite`と`IAdviseSink`します。

- 埋め込みオブジェクトまたはアクティブなドキュメントのインプレース アクティブ化をサポートします。 コンテナーのサイト オブジェクトを実装する必要があります`IOleInPlaceSite`し、コンテナーのフレーム オブジェクトを指定する必要があります`IOleInPlaceFrame`します。

- 実装によってアクティブなドキュメントの拡張機能をサポートする`IOleDocumentSite`ドキュメントと対話するコンテナーのメカニズムを提供します。 コンテナーがアクティブなドキュメントのインターフェイスを実装する必要に応じて、`IOleCommandTarget`と`IContinueCallback`を印刷または保存などの単純なコマンドを取得します。

フレーム オブジェクト、ビュー オブジェクト、およびコンテナー オブジェクトを実装できます必要に応じて`IOleCommandTarget`で説明したように、特定のコマンドのディスパッチをサポートするために[コマンド ターゲット](../mfc/message-handling-and-command-targets.md)します。 ビューとコンテナー オブジェクトを実装できますまた、必要に応じて`IPrint`と`IContinueCallback`で説明したように、プログラムによる印刷をサポートするために、[プログラムによる印刷](../mfc/programmatic-printing.md)します。

次の図は、コンテナーとそのコンポーネント (左)、およびアクティブなドキュメント (右) には、そのビューの概念の関係を示します。 アクティブなドキュメント ストレージとデータを管理して、ビューを表示、または必要に応じてそのデータを出力します。 太字でインターフェイスが; アクティブなドキュメントへの参加に必要なもの太字で斜体は省略可能です。 その他のすべてのインターフェイスが必要です。

![Active ドキュメント コンテナー インターフェイス](../mfc/media/vc37gj1.gif "vc37gj1")

1 つのビューのみをサポートするドキュメントは、ドキュメントとビューの両方のコンポーネント (つまり、対応するインターフェイス) を 1 つの具象クラスに実装できます。 さらに、のみ、一度に 1 つのビューをサポートするコンテナーのサイトに結合できます、ドキュメント サイトとサイトの表示、1 つの具体的な site クラス。 ただし、コンテナーのフレームのオブジェクトがこの distinct、維持する必要があり、アーキテクチャの全体像を提供するコンテナーのドキュメントのコンポーネントがここに単なります。active ドキュメント コンテインメントのアーキテクチャによって、影響はありません。

##  <a name="document_site_objects"></a> サイト オブジェクトのドキュメント

ドキュメント サイトでは、active ドキュメント コンテインメント アーキテクチャでは OLE ドキュメントで、追加するとクライアントのサイトのオブジェクトと同じ、`IOleDocument`インターフェイス。

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

ドキュメント サイトは、概念的には、1 つまたは複数の「ビュー サイト」オブジェクトのコンテナーです。 各ビューのサイト オブジェクトは、ドキュメント サイトで管理されているドキュメントの個々 のビュー オブジェクトに関連付けられます。 コンテナーは、ドキュメント サイトごとに 1 つのビューのみをサポートする場合を実装できますドキュメント サイトと、サイトの 1 つの具象クラスを使用します。

##  <a name="view_site_objects"></a> サイト オブジェクトの表示

コンテナーのビューのサイト オブジェクトは、ドキュメントの特定のビューの表示領域を管理します。 標準をサポートしているだけでなく`IOleInPlaceSite`インターフェイス、サイトの表示も通常、実装`IContinueCallback`の印刷をプログラムで制御します。 (注のビュー オブジェクトがないクエリを実行する`IContinueCallback`で実際に実装できるようにコンテナー要望のオブジェクトします)。

複数のビューをサポートするコンテナーは、複数のビューに、ドキュメント サイト内のサイト オブジェクトを作成できる必要があります。 これにより、それぞれのビューのアクティブ化と非アクティブ化サービスによって提供されるよう`IOleInPlaceSite`します。

##  <a name="frame_object"></a> オブジェクトの構築

コンテナーのフレーム オブジェクトは、ほとんどの場合、つまり OLE ドキュメントでは、インプレース アクティブ化に使用される同じフレーム、メニューとツールバーのネゴシエーションを処理する 1 つです。 ビュー オブジェクトが使用してこのフレーム オブジェクトへのアクセス`IOleInPlaceSite::GetWindowContext`、コンテナー ドキュメント (これは、ウィンドウ レベルのツールバーのネゴシエーションと含まれるオブジェクトの列挙体を処理することができます) を表すコンテナー オブジェクトへのアクセスを提供することもできます。

Active ドキュメント コンテナーは、追加することで、フレームを補強できます`IOleCommandTarget`します。 これにより、このインターフェイスは、同じコマンドを送信するためのコンテナーを許可するには、同じ方法でアクティブなドキュメントのユーザー インターフェイスで発生するコマンドを受信する (など**ファイル新しい**、**オープン**、 **名前を付けて**、**印刷**;**コピーして編集**、**貼り付け**、**を元に戻す**、およびその他の) アクティブなドキュメントにします。 詳細については、次を参照してください。[コマンド ターゲット](../mfc/message-handling-and-command-targets.md)します。

## <a name="see-also"></a>関連項目

[Active ドキュメント コンテインメント](../mfc/active-document-containment.md)

