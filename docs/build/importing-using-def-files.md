---
title: DEF ファイルを使用したインポート |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1562e14b20e4e1dd96764414978889d6205179
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710542"
---
# <a name="importing-using-def-files"></a>DEF ファイルを使ったインポート

使用する場合 **_declspec**と共に、.def ファイルでは、定数の代わりにデータを使用して、コーディングの誤りによってが発生する問題を低減する .def ファイルを変更する必要があります。

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

次の表では、その理由を示します。

|キーワード|インポート ライブラリに出力します。|エクスポート|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

使用して **_declspec**し、両方の定数が一覧表示、`imp`バージョンと非装飾名 .lib DLL では、明示的なリンクを許可するために作成、ライブラリをインポートします。 使用して **_declspec**とデータのリストだけ`imp`バージョンの名前。

定数を使用する場合、次のコード コンストラクトのいずれかを使用できますにアクセスする`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-または、

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

ただし、.def ファイルにデータを使用する場合、次の定義でコンパイルされたコードのみ変数アクセスできる`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

余分なレベルの間接参照を使用することを忘れてしまった場合は、変数へのインポート アドレス テーブルのポインターを可能性のあるアクセスだったためよりリスクの高いは定数を使用して、変数自体ではありません。 インポート アドレス テーブルは、現在行われるため読み取り専用のコンパイラとリンカーで、この種の問題はアクセス違反としてマニフェスト多くの場合、ことができます。

現在の Visual C リンカーは、このケースに対応する .def ファイル内の定数が見つかる場合に警告を発行します。 定数を使用する唯一の理由がのかどうか、ヘッダー ファイルが一覧表示されませんいくつかのオブジェクト ファイルを再コンパイルすることはできません **_declspec**プロトタイプ。

## <a name="see-also"></a>関連項目

[アプリケーションへのインポート](../build/importing-into-an-application.md)
