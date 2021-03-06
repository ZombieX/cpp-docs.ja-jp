---
title: 'TN048: MFC データベース アプリケーション用の ODBC セットアップおよび管理プログラムの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a70ddac1839d8967b9e9f7226a554d0b92449e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401824"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>テクニカル ノート 48: MFC データベース アプリケーション用の ODBC セットアップおよび管理プログラムの作成

> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

MFC データベース クラスを使用してアプリケーションには、ODBC コンポーネントをインストールするセットアップ プログラムを必要があります。 既定のドライバーを指定して、データ ソースを構成するのには、使用可能なドライバーについての情報を取得する ODBC の管理プログラムも必要です。 ここでは、これらのプログラムを記述する ODBC インストーラーの API の使用について説明します。

##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> ODBC セットアップ プログラムの記述

MFC データベース アプリケーション (ODBC ODBC ドライバー マネージャーが必要です。DLL) と ODBC ドライバーのデータ ソースに取得できるようにします。 多くの ODBC ドライバーでは、追加のネットワークとの通信の Dll も必要です。 ほとんどの ODBC ドライバーは ODBC に必要なコンポーネントをインストールするセットアップ プログラムに付属します。 MFC データベース クラスを使用しているアプリケーション開発者は次のとおりです。

- ODBC コンポーネントをインストールするドライバー固有のセットアップ プログラムに依存します。 これは必要がありますそれ以上、開発者の作業: ドライバーのセットアップ プログラムを再配布することだけです。

- または、ドライバー マネージャーとドライバーをインストールする独自のセットアップ プログラムを記述できます。

ODBC インストーラーの API は、アプリケーション固有のセットアップ プログラムを作成して使用できます。 ODBC インストーラー DLL によってインストーラー API 内の関数が実装されている-ODBCINST します。16 ビットの Windows と ODBCCP32 DLL です。Win32 の DLL です。 アプリケーションが呼び出すことができます`SQLInstallODBC`DLL は、ODBC ドライバー マネージャー、ODBC ドライバーでは、およびそのいずれかをインストールするインストーラーの翻訳者が必要です。 インストールされているドライバーと翻訳者が、ODBCINST で記録します。INI ファイル (または、レジストリ、NT)。 `SQLInstallODBC` ODBC への完全パスが必要です。INF ファイル、ドライバーのインストールの一覧を格納し、各ドライバーを構成するファイルについて説明します。 ドライバー マネージャーと翻訳者に関する同様の情報も含まれています。 ODBC です。通常、INF ファイルは、ドライバーの開発者によって提供されます。

プログラムでは、個々 の ODBC コンポーネントもインストールできます。 プログラムの最初の呼び出しをドライバー マネージャーをインストールする`SQLInstallDriverManager`インストーラー DLL をドライバー マネージャーのターゲット ディレクトリを取得します。 これは、通常は、Windows Dll が存在するディレクトリです。 次に、プログラムは、ODBC の [ODBC ドライバー マネージャー] セクションでは、情報を使用してください。このディレクトリにインストール ディスクからのドライバー マネージャーと関連ファイルをコピーする INF ファイルです。 プログラムの最初の呼び出し、個々 のドライバーをインストールする`SQLInstallDriver`インストーラー DLL、ODBCINST にドライバーの仕様を追加します。INI ファイル (または、レジストリ、NT)。 `SQLInstallDriver` ドライバーのターゲット ディレクトリを返します: 通常は Windows の Dll が存在するディレクトリ。 プログラムの ODBC ドライバーのセクションで情報を使用しています。このディレクトリにインストール ディスクからドライバ DLL と関連ファイルをコピーする INF ファイルです。

ODBC の詳細についてはします。INF、ODBCINST します。INI とインストーラーの API を使用して ODBC SDK を参照してください。*プログラマーズ リファレンス、* 19 章、ODBC ソフトウェアをインストールします。

##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> ODBC 管理者を作成します。

MFC データベース アプリケーションは、設定し、次のように、2 つの方法のいずれかで ODBC データ ソースを構成します。

- (プログラムまたはコントロール パネルの項目として使用可能) の ODBC アドミニストレーターを使用します。

- データ ソースを構成する独自のプログラムを作成します。

インストーラー DLL 関数の呼び出しをデータ ソースを構成するプログラムになります。 インストーラー DLL は、セットアップをデータ ソースを構成する DLL を呼び出します。 各ドライバーの 1 つのセットアップ DLL があります。ドライバー DLL 自体、または別の DLL がある可能性があります。 セットアップ DLL には、ユーザーに、ドライバーがサポートされている場合に、データ ソースと既定の変換に接続する必要がある情報メッセージが表示されます。 DLL と Windows Api は、ODBC でこの情報を記録し、インストーラーを呼び出します。INI ファイル (またはレジストリ)。

プログラムの呼び出しをユーザーは追加、変更、およびデータ ソースを削除 ダイアログ ボックスを表示するには、`SQLManageDataSources`インストーラー DLL。 インストーラー DLL は、コントロール パネルから呼び出されたときに、この関数が呼び出されます。 追加、変更、またはデータ ソースを削除する`SQLManageDataSources`呼び出し`ConfigDSN`でそのデータ ソースに関連付けられているドライバーのセットアップ DLL。 ソースの追加、変更、またはデータの削除を直接、プログラムが呼び出す`SQLConfigDataSource`インストーラー DLL。 プログラムでは、データ ソースと実行するアクションを指定するオプションの名前を渡します。 `SQLConfigDataSource` 呼び出し`ConfigDSN`セットアップ DLL から引数を渡します`SQLConfigDataSource`します。

詳細については、ODBC SDK を参照してください。*プログラマーズ リファレンス、* 第 23 章、セットアップ DLL 関数の参照、および第 24 章インストーラー DLL 関数の参照。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)

