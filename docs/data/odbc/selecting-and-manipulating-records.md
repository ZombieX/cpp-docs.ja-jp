---
title: 選択とレコードの操作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cfbeaa1fac2fd9df707dfa9c16ec168d48fc215
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078350"
---
# <a name="selecting-and-manipulating-records"></a>レコードの選択と操作

SQL を使用してデータ ソースからレコードを選択すると通常**選択**ステートメントでは、一連のテーブルまたはクエリからのレコードである結果セットを取得します。 データベース クラスでは、レコード セット オブジェクトを使用するを選択し、結果セットにアクセスします。 これはクラスから派生したアプリケーションに固有のクラスのオブジェクト[CRecordset](../../mfc/reference/crecordset-class.md)します。 レコード セット クラスを定義する場合は、それを関連付けるデータ ソース、使用するには、テーブルおよびテーブルの列を指定します。 MFC アプリケーション ウィザードまたは**クラスの追加**(」の説明に従って[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 特定のデータ ソースへの接続を持つクラスを作成します。 ウィザードの記述、 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)クラスのメンバー関数`CRecordset`テーブル名を返します。 ウィザードを使用して、レコード セット クラスを作成する方法の詳細については、次を参照してください。[データベースのサポート、MFC アプリケーション ウィザード](../../mfc/reference/database-support-mfc-application-wizard.md)と[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)します。

使用して、 [CRecordset](../../mfc/reference/crecordset-class.md) 、実行時にオブジェクトのことができます。

- 現在のレコードのデータ フィールドを確認します。

- レコード セットの並べ替えまたはフィルター処理します。

- 既定の SQL のカスタマイズ**選択**ステートメント。

- 選択されたレコードをスクロールします。

- 追加、更新、または (データ ソースとレコード セットの両方が更新可能な) 場合は、レコードを削除します。

- レコード セットのクエリを再実行ができるかどうかをテストし、レコード セットの内容を更新します。

レコード セット オブジェクトの使用が完了したらを閉じるし、それを破棄します。 レコード セットの詳細については、次を参照してください。[レコード セット (ODBC)](../../data/odbc/recordset-odbc.md)します。

## <a name="see-also"></a>関連項目

[ODBC と MFC](../../data/odbc/odbc-and-mfc.md)