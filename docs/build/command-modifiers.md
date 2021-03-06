---
title: コマンド修飾子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd86adc94de90222e0775d89543a4dc25486f74f
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894500"
---
# <a name="command-modifiers"></a>コマンド修飾子

上記のコマンドは、必要に応じてスペースまたはタブで区切られた 1 つまたは複数のコマンド修飾子を指定することができます。 コマンドと同様、修飾子をインデントする必要があります。

|修飾子|目的|
|--------------|-------------|
|\@*コマンド*|コマンドが表示されなくなります。 コマンドによる表示は削除されません。 既定では、(nmake の) は、実行されたすべてのコマンドをエコーします。 /S を使用して、メイクファイル全体の表示を抑制するには使用して、**します。サイレント**メイクファイルのパーツの表示を抑制します。|
|**-**\[*数*]*コマンド*|エラー チェックをオフに*コマンド*します。 既定では、(nmake の) は、コマンドには 0 以外の終了コードが返されるときに停止します。 If -*数*が使用すると、NMAKE を停止、終了コードを超えた場合*数*します。 スペースまたはタブがダッシュ ボード間表示ことはできませんと*数。* 間に少なくとも 1 つのスペースまたはタブが表示する必要があります`number`と*コマンド*します。 /I を使用して、メイクファイル全体のエラー チェックをオフにします。使用して、**します。無視**メイクファイルの一部のエラー チェックをオフにします。|
|**!** *command*|実行*コマンド*各依存ファイルの場合*コマンド*使用<strong>$ \* \*</strong> (すべての依存ファイルで、依存関係) または **$?** (すべての依存ファイルでターゲットよりも後のタイムスタンプを持つ依存関係)。|

## <a name="see-also"></a>関連項目

[メイクファイルのコマンド](../build/commands-in-a-makefile.md)
