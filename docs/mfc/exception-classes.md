---
title: 例外クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.exception
dev_langs:
- C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd666f96ed694b57bf02eb3ad239783828b69e48
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439264"
---
# <a name="exception-classes"></a>例外クラス

クラス ライブラリには、クラスに基づいた例外処理メカニズム`CException`します。 アプリケーション フレームワークでは、コードで例外を使用します。独自のコードに使用することもできます。 詳細については、この記事を参照してください。[例外](../mfc/exception-handling-in-mfc.md)します。 独自の例外型を派生する`CException`します。

MFC では、すべてのサポートの例外の例外クラスと同様に、独自の例外の派生元となる例外クラスを提供します。

[CException](../mfc/reference/cexception-class.md)<br/>
例外の基底クラス。

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
アーカイブの例外。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
DAO データベース操作の失敗による例外です。

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
ODBC データベースの処理中のエラーによる例外。

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
ファイル指向の例外。

[CMemoryException](../mfc/reference/cmemoryexception-class.md)<br/>
メモリ不足の例外。

[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)<br/>
サポートされていない機能を使用して結果である例外。

[COleException](../mfc/reference/coleexception-class.md)<br/>
OLE の処理中のエラーによる例外。 このクラスは、コンテナーとサーバーの両方で使用されます。

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Automation の中にエラーによる例外。 Automation の例外はオートメーション サーバーによってスローされ、オートメーション クライアントによってキャッチします。

[CResourceException](../mfc/reference/cresourceexception-class.md)<br/>
Windows リソースの読み込みに失敗による例外です。

[CUserException](../mfc/reference/cuserexception-class.md)<br/>
使用して、ユーザーが開始した操作を停止する例外。 通常、ユーザーに通知されました、問題の前に、この例外がスローされます。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)

