---
title: インライン ファイルの指定 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73983094f10088920100b4fbbb8d870aee13f05e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720565"
---
# <a name="specifying-an-inline-file"></a>インライン ファイルの指定

2 つの山かっこを指定 (<<) コマンドで、 *filename*が表示されます。 山かっこでは、マクロの展開をすることはできません。

## <a name="syntax"></a>構文

```
<<[filename]
```

## <a name="remarks"></a>Remarks

山かっこは置き換えられますコマンドが実行される*filename*、指定されている場合や (nmake の) によって生成された一意の名前。 指定した場合*filename*スペースまたはタブを使用せず、山かっこに従う必要があります。パスが許可されます。 拡張子のが必須かまたはと見なされません。 場合*filename*指定すると、現在のファイルを作成または指定されたディレクトリは、その名前でファイルの既存のすべての上書きは TMP ディレクトリに作成された場合は、(現在のディレクトリ、または場合 TMP 環境変数定義されていません)。 場合は、以前*filename*は NMAKE 再利用すると、前のファイルを置き換えます。

## <a name="see-also"></a>関連項目

[メイクファイルのインライン ファイル](../build/inline-files-in-a-makefile.md)