---
title: 'ブラウザー情報ファイルのビルド: 概要 |マイクロソフトのドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 493f25ba6839058a9ff749cb0dbb3853b1b16494
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712297"
---
# <a name="building-browse-information-files-overview"></a>ブラウザー情報ファイルのビルド : 概要

シンボル参照の参照情報を作成するには、コンパイラは、BSCMAKE では、プロジェクトでソース ファイルごとに、.sbr ファイルを作成します。EXE は .bsc ファイルの 1 つに、.sbr ファイルを連結します。

.Sbr ファイルと .bsc ファイルを生成する、時間がかかるため、Visual C は、既定でオフこれらの関数にします。 を現在の情報を参照する場合は、参照オプションをオンにして、プロジェクトをもう一度ビルドする必要があります。

使用[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)または[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) .sbr ファイルを作成するようにコンパイラに指示します。 .Bsc ファイルを作成するを呼び出すことができます[BSCMAKE](../../build/reference/bscmake-command-line.md)コマンドラインから。 BSCMAKE コマンドラインから使用するブラウザー情報ファイルの操作をより正確に制御します。 参照してください[BSCMAKE リファレンス](../../build/reference/bscmake-reference.md)詳細についてはします。

> [!TIP]
>  .Bsc ファイルの生成がオフのままには、.sbr ファイルの生成を有効にすることができます。 これにより、高速のビルドは .bsc ファイルの生成をオンにし、プロジェクトをビルドして、新しい .bsc ファイルをすばやく作成することもできます。

時間、メモリ、および .bsc ファイルのサイズを小さくして .bsc ファイルのビルドに必要なディスク領域を減らすことができます。

参照してください[[全般] プロパティ ページ (プロジェクト)](../../ide/general-property-page-project.md)については、開発環境でのブラウザー ファイルを作成する方法。

### <a name="to-create-a-smaller-bsc-file"></a>サイズの小さい .bsc ファイルを作成するには

1. 使用[BSCMAKE コマンド ライン オプション](../../build/reference/bscmake-options.md)ブラウザー情報ファイルから情報を除外します。

1. コンパイルまたはアセンブルすると、.sbr ファイルの 1 つまたは複数のローカルのシンボルを除外します。

1. オブジェクト ファイルに、現在のステージのデバッグに必要な情報が含まれていない場合は、ブラウザー情報ファイルを再構築するときに、BSCMAKE コマンドから、.sbr ファイルを省略します。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>1 つのブラウザー ファイル (.bsc) にいくつかのプロジェクトから参照情報を結合するには

1. いずれかが、プロジェクト レベルで .bsc ファイルをビルドまたは .sbr ファイルが切り詰められていることを防ぐために、/n スイッチを使用しないでください。

1. すべてのプロジェクトをビルドすると後、は、入力としてのすべての .sbr ファイルで BSCMAKE を実行します。 ワイルドカードを使用します。 たとえば、プロジェクト ディレクトリ C:\X、C:\Y、C:\Z すべて .bsc ファイルの 1 つに結合するときのそれらの .sbr ファイルがある場合、使用 BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\\*.sbr の/o c:\whatever_directory\combined.bsc 結合された .bsc ファイルをビルドします。

## <a name="see-also"></a>関連項目

[C/C++ のビルド ツール](../../build/reference/c-cpp-build-tools.md)<br/>
[BSCMAKE リファレンス](../../build/reference/bscmake-reference.md)
