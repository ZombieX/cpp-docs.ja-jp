---
title: テキスト ストリームとバイナリ ストリーム | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 106e02de80c3132846d7b88161637a37f74a59ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068638"
---
# <a name="text-and-binary-streams"></a>テキスト ストリームとバイナリ ストリーム

テキスト ストリームは、読むことができるように、テキスト指向の表示として書き込まれた 1 行または複数行のテキストで構成されます。 テキスト ストリームから読み取る場合、プログラムは各行の末尾で `NL` を読み取ります。 テキスト ストリームに書き込む場合は、プログラムは行の末尾を示すために `NL` を書き込みます。 ファイル内のテキストを表現するためのターゲット環境間で異なる規則を一致させるために、ライブラリ関数が、プログラムとテキスト ストリームの間で送信される文字の表現と数を変更することがあります。

したがって、テキスト ストリーム内の位置決めには、制限があります。 現在のファイル位置インジケーターは、[fgetpos](../c-runtime-library/reference/fgetpos.md) または [ftell](../c-runtime-library/reference/ftell-ftelli64.md) を呼び出すことで取得できます。 この方法で取得された位置に、または[fsetpos](../c-runtime-library/reference/fsetpos.md) や [fseek](../c-runtime-library/reference/fseek-fseeki64.md) を呼び出すことでストリームの先頭または末尾に、テキスト ストリームを配置できます。 その他の配置の変更はサポートされていません。

移植性を最大化するために、プログラムで以下を記述しないでください。

- 空のファイル。

- 行の末尾のスペース文字。

- 不完全な行 (ファイルの最後の `NL` を省略する)。

- 印刷可能な文字、NL、`HT` (水平タブ) 以外の文字。

これらの規則に従うと、テキスト ストリームから読み取る文字のシーケンス (バイトまたはマルチバイト文字のどちらかとして) が、ファイル作成時にテキスト ストリームに書き込んだ文字のシーケンスと一致します。 そうしないと、作成したファイルを閉じるときにファイルが空の場合、ライブラリ関数によって該当ファイルが削除されることがあります。 または、ファイルに書き込む文字が変更されたり削除されたりすることがあります。

バイナリ ストリームは、1 バイトまたは複数バイトの任意の情報で構成されます。 (バイト指向の) バイナリ ストリームに任意のオブジェクトに格納されている値を書き込み、書き込んだ際にオブジェクトに格納された内容を正確に読み取ることができます。 ライブラリ関数では、プログラムとバイナリ ストリームの間で送信するバイトは変更されません。 ただし、バイナリ ストリームで書き込むファイルに任意の数の null バイトが追加されることがあります。 プログラムでは、バイナリ ストリームの末尾に追加されるこれらの null バイトを扱う必要があります。

そうすることで、ストリームの末尾からの相対位置を除く、バイナリ ストリーム内の位置決めが適切に定義されます。 現在のファイル位置インジケーターは、テキスト ストリームの場合と同じ方法で、取得および変更できます。 さらに、[ftell](../c-runtime-library/reference/ftell-ftelli64.md) と [fseek](../c-runtime-library/reference/fseek-fseeki64.md) で使用されるオフセットは、ストリームの先頭 (0 バイト目) からのバイト数をカウントするため、このオフセットを整数演算することで、予測可能な結果が得られます。

バイト ストリームはバイトのシーケンスとしてファイルを扱います。 プログラム内では、ストリームは、前述の差異がある可能性を除き、同一のバイトのシーケンスのように見えます。

## <a name="see-also"></a>参照

[ファイルとストリーム](../c-runtime-library/files-and-streams.md)