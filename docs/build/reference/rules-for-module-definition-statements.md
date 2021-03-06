---
title: モジュール定義ステートメントに関する規則 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- .def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a31927bb1ce3667367eff8f38268b4b3b24ac82c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726480"
---
# <a name="rules-for-module-definition-statements"></a>モジュール定義ステートメントに関する規則

次の構文規則は、.def ファイル内のすべてのステートメントに適用されます。 特定のステートメントに適用されるその他の規則は、それぞれのステートメントについて説明します。

- ステートメント、属性のキーワード、およびユーザー指定の識別子が大文字小文字を区別します。

- 長いファイル名を空白またはセミコロン (;) を格納している引用符 (") で囲む必要があります。

- ステートメントのキーワードをその引数から分離して、互いからステートメントを区切るために、スペース、タブ、または改行文字の 1 つまたは複数を使用します。 コロン (:) または等号 (=) の引数を指定するは 0 以上のスペース、タブ、または改行文字で囲みます。

- A**名前**または**ライブラリ**ステートメントでは、使用する場合の他のすべてのステートメント必要があります前にします。

- **セクション**と**エクスポート**.def ファイル内のステートメントが複数回出現できます。 各ステートメントには、複数の仕様は、1 つまたは複数のスペース、タブ、または改行文字で区切る必要がありますがかかることができます。 ステートメントのキーワードでは、最初の指定の前に 1 回記述する必要があり、各追加指定の前に繰り返すことができます。

- 多くのステートメントでは、同等のリンク コマンド ライン オプションがあります。 詳細については、対応するリンク オプションの説明を参照してください。

- .Def ファイル内のコメントはセミコロン (;) で指定されたそれぞれのコメント行の先頭にします。 コメントはステートメントでは、回線を共有することはできませんが、複数のステートメントの仕様間に表示できます。 (**セクション**と**エクスポート**は複数行ステートメントです)。

- 数値の引数が 10 進数で指定されたか、16 進数です。

- 文字列引数と一致する場合、[予約語](../../build/reference/reserved-words.md)、これは、二重引用符 (") で囲む必要があります。

## <a name="see-also"></a>関連項目

[モジュール定義 (.def) ファイル](../../build/reference/module-definition-dot-def-files.md)