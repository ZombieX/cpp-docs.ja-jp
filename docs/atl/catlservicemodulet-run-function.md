---
title: Catlservicemodulet::run 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f7306e11bd1cc23e4de17e67f0941d2b3ee8473
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055296"
---
# <a name="catlservicemoduletrun-function"></a>Catlservicemodulet::run 関数

`Run` 呼び出しを含む`PreMessageLoop`、 `RunMessageLoop`、および`PostMessageLoop`します。 呼び出された後に`PreMessageLoop`最初に、サービスのスレッドの ID を格納します サービスは、この ID を使用して、Win32 API 関数を使用して WM_QUIT メッセージを送信することによってそれ自体を閉じるには[次](https://msdn.microsoft.com/library/windows/desktop/ms644946)します。

`PreMessageLoop` 呼び出して`InitializeSecurity`します。 既定では、`InitializeSecurity`呼び出し[CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity)を NULL に設定するセキュリティ記述子、つまり、ユーザーが、オブジェクトへのアクセスを持っています。

独自のセキュリティを指定するサービスしたくない場合は、オーバーライド`PreMessageLoop`呼び出さないでください`InitializeSecurity`COM がし、レジストリからのセキュリティ設定を確認します。 レジストリ設定を構成する便利な方法は、 [DCOMCNFG](../atl/dcomcnfg.md)ユーティリティのこのセクションで後ほど説明します。

セキュリティを指定すると、プログラムに新しいクライアントが接続できるようにを COM オブジェクトが登録されています。 最後に、プログラムが実行されていることと、メッセージ ループに入るプログラム、サービス コントロール マネージャー (SCM) に指示します。 サービスのシャット ダウン時に quit メッセージを投稿するまで、プログラムを実行したままです。

## <a name="see-also"></a>関連項目

[サービス](../atl/atl-services.md)<br/>
[CSecurityDesc クラス](../atl/reference/csecuritydesc-class.md)<br/>
[CSid クラス](../atl/reference/csid-class.md)<br/>
[CDacl クラス](../atl/reference/cdacl-class.md)<br/>
[Catlservicemodulet::run](../atl/reference/catlservicemodulet-class.md#run)

