---
title: ODBC アドミニストレーター |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c00527b5378805e0aa81c74c23175edd39bd144
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052578"
---
# <a name="odbc-administrator"></a>ODBC データ ソース アドミニストレーター

ODBC アドミニストレーターが登録され、構成されます、[データ ソース](../../data/odbc/data-source-odbc.md)使用できるローカルまたはネットワーク上でします。 ウィザードは、ODBC データ ソース アドミニストレーターの提供する情報を利用して、データ ソースに接続するコードを生成します。

MFC ODBC クラスまたは MFC DAO (データ アクセス オブジェクト) クラスで使用する ODBC データ ソースをセットアップするには、最初にデータ ソースの登録と設定を行う必要があります。 データ ソースの追加や削除には ODBC データ ソース アドミニストレーターを使います。 使用する ODBC ドライバーによっては、新しいデータ ソースも作成できます。

ODBC データ ソース アドミニストレーターは、セットアップ時にインストールされます。 選択した場合**カスタム**インストールで ODBC ドライバーを選択していないと、**データベース オプション**ダイアログ ボックスで、必要なファイルをインストールするには、もう一度セットアップを実行する必要があります。

ODBC ドライバーは、セットアップ時に選択してインストールします。 また、セットアップ後に、Visual C++ セットアップ プログラムを使って、Visual C++ に添付されているドライバーをインストールすることもできます。

Visual C++ に添付されていない ODBC ドライバーをインストールする場合は、そのドライバーのセットアップ プログラムを実行してください。

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Visual C++ に添付されている ODBC ドライバーをインストールするには

1. Visual C++ の CD からセットアップ プログラムを起動します。

   セットアップ プログラムの最初のダイアログ ボックスが表示されます。

1. クリックして**次**に到達するまでは、各ダイアログ ボックスで、**インストール オプション** ダイアログ ボックス。 選択**カスタム**、 をクリックし、**次**。

1. すべてのチェック ボックスをオフ、 **Microsoft Visual C のセットアップ**以外のダイアログ ボックス、**データベース オプション**チェック ボックスをオンにして**詳細**を表示する**データベース オプション** ダイアログ ボックス。

1. クリア、 **Microsoft Data Access Objects**チェック ボックスをオン、 **Microsoft ODBC Drivers**チェック ボックスをオンにして**詳細**します。

   **Microsoft ODBC Drivers**  ダイアログ ボックスが表示されます。

1. ドライバーをインストールし、をクリックする を選択**OK** 2 回クリックします。

1. をクリックして**次**インストールを開始する残りのダイアログ ボックスでします。 インストールが完了すると、セットアップ プログラムが知らせます。

ドライバーをインストールしたら、ODBC データ ソース アドミニストレーターを使用してデータ ソースを設定できます。 ODBC アイコンはコントロール パネルにあります。

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)