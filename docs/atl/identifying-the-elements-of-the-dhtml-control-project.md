---
title: DHTML コントロール プロジェクトの要素の識別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 868feab383c324962c05fc5e341092cf89f895f5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752834"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>DHTML コントロール プロジェクトの要素の識別

DHTML コントロールのほとんどのコードが正確にそのような ATL コントロールに対して作成されます。 ジェネリック コードの基本を理解するには、を通じて動作、 [ATL チュートリアル](../atl/active-template-library-atl-tutorial.md)、セクションを参照して[ATL プロジェクトの作成](../atl/reference/creating-an-atl-project.md)と[ATL COM オブジェクトの基本事項](../atl/fundamentals-of-atl-com-objects.md)します。

DHTML コントロールは、ATL コントロールに似ていますを除く。

- コントロールが実装する標準のインターフェイスだけでなく、C++ コードと HTML ユーザー インターフェイス (UI) の間の通信に使用される追加のインターフェイスを実装します。 HTML UI は、このインターフェイスを使用して C++ コードを呼び出します。

- UI コントロールの HTML リソースを作成します。

- メンバー変数を使用して、DHTML オブジェクト モデルへのアクセスを許可`m_spBrowser`、型のスマート ポインターである[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)します。 DHTML オブジェクト モデルの一部にアクセスするのにには、このポインターを使用します。

次の図は、DLL、DHTML コントロール、Web ブラウザー、および HTML リソース間のリレーションシップを示しています。

![DHTML コントロール プロジェクトの要素](../atl/media/vc52en1.gif "vc52en1")

> [!NOTE]
>  このグラフィックの名前は、プレース ホルダーです。 HTML のリソースと、コントロールに公開されるインターフェイスの名前は、ATL コントロール ウィザードで割り当てた名前に基づいています。

次の図の要素は。

- **DLL** ATL プロジェクト ウィザードを使用して作成された DLL です。

- **DHTML コントロール**(`m_spBrowser`)、DHTML コントロール、ATL オブジェクト ウィザードを使用して作成します。 このコントロールは、Web ブラウザーのオブジェクトのインターフェイスを使用して Web ブラウザーのオブジェクトとそのメソッドにアクセス`IWebBrowser2`します。 コントロール自体では、コントロールに必要なその他の標準のインターフェイスに加えて、次の 2 つインターフェイスを公開します。

   - `IDHCTL1` コンテナーでのみ使用するためのコントロールによって公開されるインターフェイス。

   - `IDHCTLUI1` C++ コードと HTML ユーザー インターフェイスの間の通信のディスパッチ インターフェイス。 Web ブラウザーでは、コントロールを表示するのにコントロールのディスパッチ インターフェイスを使用します。 呼び出すことによって、コントロールのユーザー インターフェイスからこのディスパッチ インターフェイスのさまざまなメソッドを呼び出すことができます`window.external`、その後に呼び出すこのディスパッチ インターフェイスでメソッド名。 アクセスするには`window.external`このコントロールの UI を構成する HTML 内のスクリプト タグから。 リソース ファイル内の外部メソッドの呼び出しの詳細については、次を参照してください。 [DHTML から C++ コードを呼び出す](../atl/calling-cpp-code-from-dhtml.md)します。

- **IDR_CTL1** HTML リソースのリソース ID。 そのファイル名では、DHCTL1UI.htm ここでは。 DHTML コントロールは、標準の HTML タグとテキスト エディターを使用して編集可能な外部ウィンドウ ディスパッチ コマンドを含む HTML リソースを使用します。

- **Web ブラウザー** Web ブラウザーが HTML のリソースに html 形式で、コントロールの UI を表示します。 Web ブラウザーへのポインター`IWebBrowser2`インターフェイスは、DHTML オブジェクト モデルへのアクセスを許可する DHTML コントロールで使用できます。

ATL コントロール ウィザードでは、HTML リソースおよび .cpp ファイルの両方で既定のコードを使用して、コントロールを生成します。 コンパイルし、ウィザードによって生成されると、コントロールを実行して、Web ブラウザーまたは ActiveX コントロール テスト コンテナーのいずれかで、コントロールを表示できます。 次の図は、テスト コンテナーに表示される 3 つのボタンで ATL DHTML コントロールの既定値を示しています。

![ATL DHTML コントロール](../atl/media/vc52en2.gif "vc52en2")

参照してください[ATL DHTML コントロールの作成](../atl/creating-an-atl-dhtml-control.md)DHTML コントロールの構築を開始します。 参照してください[テスト プロパティとテスト コンテナーでイベント](../mfc/testing-properties-and-events-with-test-container.md)テスト コンテナーにアクセスする方法についてはします。

## <a name="see-also"></a>関連項目

[DHTML コントロールのサポート](../atl/atl-support-for-dhtml-controls.md)

