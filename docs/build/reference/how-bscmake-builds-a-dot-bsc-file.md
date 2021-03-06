---
title: BSCMAKE のビルド方法、します。Bsc ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aadf3b29b0714cc47850e177ebe6e1d0e54df784
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719434"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>BSCMAKE による .bsc ファイルのビルド方法

BSCMAKE では、ビルドまたは .bsc ファイルが、最も効率的な方法で再構築されます。 潜在的な問題を回避するには、ビルド プロセスを理解する必要があります。

BSCMAKE では、ブラウザー情報ファイルをビルド、長さ 0 に .sbr ファイルが切り捨てられます。 同じファイルの後続のビルド中には、長さが 0 (または空) の .sbr ファイルは、.sbr ファイルに新しい情報がないことを BSCMAKE に通知します。 BSCMAKE には、ファイルの部分の更新プログラムは不要であり、インクリメンタル ビルドが十分になりますことができます。 すべてのビルド中に (/n オプションが指定されていない場合)、BSCMAKE が最初に変更された .sbr ファイルのみを使用してファイルを増分更新を試みます。

BSCMAKE では、/o オプションで指定された名前を持つ .bsc ファイルを探します。 /O が指定されていない場合、BSCMAKE は、最初の .sbr ファイルと拡張子 .bsc で構成の基本の名前を持つファイルを探します。 ファイルが存在する場合、提供する .sbr ファイルのみを使用してブラウザー情報ファイルのインクリメンタル ビルドが実行されます。 ファイルが存在しない場合、BSCMAKE は、すべての .sbr ファイルを使用してフル ビルドを実行します。 ビルドの規則は次のとおりです。

- 成功するフル ビルド、.sbr ファイルが存在する必要があり、切り捨てられませんする必要がありますすべて指定します。 .Sbr ファイルが切り捨てられる場合は、BSCMAKE を実行する前に (再コンパイルまたはアセンブル) をリビルドする必要があります。

- インクリメンタル ビルドを成功させる、.bsc ファイルが存在する必要があります。 関係しているすべての .sbr ファイルは、空のファイルがあってが存在し、BSCMAKE コマンドラインで指定する必要があります。 コマンドラインから .sbr ファイルを省略すると、BSCMAKE は、ファイルから、投稿物を削除します。

## <a name="see-also"></a>関連項目

[.bsc ファイルのビルド](../../build/reference/building-a-dot-bsc-file.md)