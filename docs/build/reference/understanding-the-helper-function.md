---
title: ヘルパー関数について |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90ca214b28296417ab80341232c08a55b92adff4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725493"
---
# <a name="understanding-the-helper-function"></a>ヘルパー関数について

リンカーでサポートされている遅延読み込みヘルパー関数は、何を実際に実行時に、DLL を読み込みます。 Delayimp.lib で提供されているヘルパー関数を使用する代わりに、プログラムにリンクすることを独自の関数を作成してその動作をカスタマイズするヘルパー関数を変更することができます。 1 つのヘルパー関数では、すべての遅延読み込み Dll は機能します。

DLL またはインポートの名前に基づく特定の処理を実行する場合は、独自のバージョンのヘルパー関数を提供できます。

ヘルパー関数は、次の操作を実行します。

- 読み込まれた既にかどうかに表示するライブラリを識別するハンドル ストアドを確認します。

- 呼び出し**LoadLibrary** DLL の読み込みを試行するには

- 呼び出し**GetProcAddress**プロシージャのアドレスの取得を試行するには

- 遅延インポートを返します。 読み込むサンクを今すぐ読み込むエントリ ポイントを呼び出す

ヘルパー関数は、次の操作のそれぞれの後、プログラムで通知フックにコールバックできます。

- ヘルパー関数が起動したとき

- 直前に**LoadLibrary**はヘルパー関数で呼び出されます

- 直前に**GetProcAddress**はヘルパー関数で呼び出されます

- 場合に呼び出し**LoadLibrary**ヘルパー関数が失敗しました

- 場合に呼び出し**GetProcAddress**ヘルパー関数が失敗しました

- ヘルパー関数が終了処理

これらの各フック ポイントに遅延インポート ロード サンクを返す以外の何らかの形でヘルパー ルーチンの通常の処理を変更する値を返すことができます。

既定のヘルパー コードは、Delayhlp.cpp と Delayimp.h (vc\include) 内にあることができますあり、Delayimp.lib で (vc\lib) でコンパイルしています。 独自のヘルパー関数を記述しない限り、コンパイル時にこのライブラリを含める必要があります。

次のトピックでは、ヘルパー関数について説明します。

- [Visual C++ 6.0 以降の DLL 遅延読み込みヘルパー関数の変更点](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [呼び出し規約、パラメーター、および戻り値の型](../../build/reference/calling-conventions-parameters-and-return-type.md)

- [構造体と定数の定義](../../build/reference/structure-and-constant-definitions.md)

- [必要な値の計算](../../build/reference/calculating-necessary-values.md)

- [遅延読み込みした DLL のアンロード](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>関連項目

[リンカーによる DLL の遅延読み込み](../../build/reference/linker-support-for-delay-loaded-dlls.md)