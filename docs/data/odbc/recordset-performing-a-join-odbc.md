---
title: 'レコード セット: 結合 (ODBC) を実行する |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60a2a06e5b6f2ba72c0cf5c7997a20e5df88d7e6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062146"
---
# <a name="recordset-performing-a-join-odbc"></a>レコードセット: 結合 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

## <a name="what-a-join-is"></a>どのような結合とは

結合操作、データ アクセスの一般的なタスクを使用して 1 つのレコード セット オブジェクトを使用して 1 つ以上のテーブルからデータを操作できます。 2 つ以上のテーブルを結合すると、各テーブルから列を含めることができますが、アプリケーションに 1 つのテーブルとして表示されるレコード セットが生成されます。 結合が、すべてのテーブルが、SQL のすべての列を使用することもあります**選択**結合句では、各テーブルの列の一部のみを使用します。 データベース クラスでは、読み取り専用の結合が、更新不可の結合をサポートします。

結合テーブルから列を含むレコードを選択するには、次のものが必要です。

- 結合されるすべてのテーブルの名前を含むテーブルの一覧。

- 参加しているすべての列の名前を含む列のリストです。 列の名前が同じ名前が異なるテーブルからは、テーブル名で修飾されます。

- フィルター (SQL**場所**句)、テーブルが参加している列を指定します。 このフィルターは"Table1.KeyCol テーブル 2. 基準列を ="、実際には、結合を行うことができます。

同じ方法で 2 つ以上のテーブルを結合するには列の複数のペア、SQL キーワード、参加させる各ペアが等しいか調査して**AND**します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: 定義済みクエリを利用したクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[レコードセット: テーブルにアクセスするレコードセット クラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[レコードセット: クエリの再実行 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)