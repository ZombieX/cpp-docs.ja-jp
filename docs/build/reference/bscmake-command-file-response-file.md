---
title: BSCMAKE コマンド ファイル (応答ファイル) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69fb144bed21b00fc07107f3fa8d5e64c1afb10d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716563"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE コマンド ファイル (応答ファイル)

コマンド ファイルでは、コマンドラインの入力の一部またはすべてを行うことができます。 次の構文を使用してコマンド ファイルを指定します。

```
BSCMAKE @filename
```

1 つのコマンド ファイルが許可されます。 パスを指定する*filename*します。 前に*filename*で、アット マーク (**\@**)。 BSCMAKE では、拡張機能は想定しません。 追加を指定できます*sbrfiles*後のコマンド ラインで*filename*します。 コマンド ファイルは、コマンドラインで指定する場合と同じ順序では、BSCMAKE への入力を含むテキスト ファイルです。 コマンドライン引数を 1 つまたは複数のスペース、タブ、または改行文字で区切ります。

次のコマンドは、BSCMAKE コマンド ファイルを使用して呼び出します。

```
BSCMAKE @prog1.txt
```

コマンド ファイルのサンプルを次に示します。

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>関連項目

[BSCMAKE リファレンス](../../build/reference/bscmake-reference.md)