---
title: C/C++ プログラムのマニフェスト生成の理解 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91120d1c8485d43a447310440bbe0bab8f7e3b75
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726259"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>C/C++ プログラムのマニフェスト生成についての理解

A[マニフェスト](https://msdn.microsoft.com/library/aa375365)はアプリケーションまたはアセンブリ内、外部の XML ファイルまたはリソースが可能な XML ドキュメントに埋め込まれます。 マニフェストを[分離アプリケーション](/windows/desktop/SbsCs/isolated-applications)名前と、アプリケーションから実行時にバインドする共有のサイド バイ サイド アセンブリのバージョンを管理するために使用します。 サイド バイ サイド アセンブリのマニフェストでは、名前、バージョン、リソース、およびその他のアセンブリをその依存関係を指定します。

分離アプリケーションまたはサイド バイ サイド アセンブリのマニフェストを作成する 2 つの方法はあります。 最初に、アセンブリの作成者は、次の規則と名前付けに関する要件のマニフェスト ファイルを手動で作成できます。 または、プログラムがのみ CRT、MFC、ATL、または他のユーザーなどの Visual C のアセンブリを依存している場合、マニフェストを生成できます自動的に、リンカーによって。

Visual C ライブラリのヘッダーには、アセンブリ情報が含まれ、最終的なバイナリのマニフェストを形成する、リンカーによってこのアセンブリ情報が使用されるアプリケーション コードでは、ライブラリが含まれている、ときにします。 リンカーは、バイナリ内のマニフェスト ファイルが埋め込まれません、のみを外部ファイルとしてマニフェストを生成できます。 外部ファイルとしてマニフェストを持つすべてのシナリオは機能しません。 たとえば、プライベート アセンブリのマニフェストが埋め込まれたことをお勧めします。 コードをビルドする nmake を使用するようなコマンド ライン ビルドでマニフェストを埋め込むことができます。 マニフェストのツールを使用して詳細については、次を参照してください。[コマンドラインでマニフェストの生成](../build/manifest-generation-at-the-command-line.md)します。 マニフェスト ツールのプロパティを設定して、マニフェストを埋め込むことが Visual Studio でビルドする場合、**プロジェクトのプロパティ**ダイアログ; を参照してください[Visual Studio でのマニフェスト生成](../build/manifest-generation-in-visual-studio.md)します。

## <a name="see-also"></a>関連項目

[分離アプリケーションおよび side-by-side アセンブリの概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)