---
title: 新しいドキュメント、Windows、およびビューを作成する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b4ccddbed0d347468331218614cad70cfd49a62
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427239"
---
# <a name="creating-new-documents-windows-and-views"></a>新しいドキュメント、ウィンドウ、ビューの作成

次の図は、ドキュメント、ビュー、およびフレーム ウィンドウの作成プロセスの概要を提供します。 参加しているオブジェクトに焦点を他の記事さらに詳細を提供します。

このプロセスを完了したら、協調動作するオブジェクトが存在し、相互へのポインターを格納します。 次の図は、オブジェクトが作成されるシーケンスを示しています。 図、シーケンスを実行できます。

![ドキュメントを作成するためのシーケンス](../mfc/media/vc387l1.gif "vc387l1")ドキュメントの作成過程

![フレーム ウィンドウ作成順序](../mfc/media/vc387l2.png "vc387l2")フレーム ウィンドウの作成過程

![ビューを作成するシーケンス](../mfc/media/vc387l3.gif "vc387l3")ビューの作成過程

フレームワークが新しいドキュメント、ビュー、およびフレーム ウィンドウ オブジェクトを初期化する方法については、クラスを参照してください[CDocument](../mfc/reference/cdocument-class.md)、 [CView](../mfc/reference/cview-class.md)、 [CFrameWnd](../mfc/reference/cframewnd-class.md)、 [。CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)、および[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) MFC ライブラリのリファレンス。 参照してください[テクニカル ノート 22:](../mfc/tn022-standard-commands-implementation.md)、その説明のフレームワークの標準コマンドの作成および初期化プロセスがさらに説明しています、**新規**と**を開く**上の項目、**ファイル**メニュー。

##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> これらのクラスに、独自の追加の初期化

上記の図では、位置には、アプリケーションのオブジェクトを初期化するためにメンバー関数をオーバーライドできるポイントも提示されます。 オーバーライドを`OnInitialUpdate`ビューのクラスは、ビューを初期化するために最適な場所。 `OnInitialUpdate`フレーム ウィンドウが作成され、フレーム ウィンドウ内のビューがそのドキュメントにアタッチされた直後後に呼び出しが発生します。 たとえば、ビューには、スクロール ビュー (から派生した`CScrollView`なく`CView`) のドキュメントのサイズに基づくビューのサイズを設定する必要があります、`OnInitialUpdate`をオーバーライドします。 (このプロセスは、クラスの説明に記載されて[CScrollView](../mfc/reference/cscrollview-class.md))。オーバーライドすることができます、`CDocument`メンバー関数`OnNewDocument`と`OnOpenDocument`ドキュメントのアプリケーション固有の初期化を提供します。 通常、2 つの方法でドキュメントを作成できますから両方をオーバーライドする必要があります。

ほとんどの場合、オーバーライドは基本クラスのバージョンを呼び出す必要があります。 詳細については、クラスの名前付きのメンバー関数を参照してください[CDocument](../mfc/reference/cdocument-class.md)、 [CView](../mfc/reference/cview-class.md)、 [CFrameWnd](../mfc/reference/cframewnd-class.md)、および[CWinApp](../mfc/reference/cwinapp-class.md) 、MFC の。ライブラリの参照。

## <a name="see-also"></a>関連項目

[ドキュメント テンプレートとドキュメント/ビューの作成手順](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[ドキュメント テンプレートの作成](../mfc/document-template-creation.md)<br/>
[ドキュメント/ビューの作成](../mfc/document-view-creation.md)<br/>
[各種 MFC オブジェクト間の関係](../mfc/relationships-among-mfc-objects.md)

