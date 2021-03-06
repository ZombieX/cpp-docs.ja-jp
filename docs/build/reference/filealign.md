---
title: /FILEALIGN (ファイルのセクションの配置) |Microsoft Docs
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 630fe7014c87487a9b4df61de60ac8f5518593e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720019"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN (ファイルのセクションの配置)

**/FILEALIGN**リンカー オプションを使用して、指定のサイズの倍数として、出力ファイルに書き込まれるセクションの配置を指定できます。

## <a name="syntax"></a>構文

> __/FILEALIGN:__*サイズ*

### <a name="parameters"></a>パラメーター

*size*<br/>
2 の累乗である必要があります (バイト) セクションの配置のサイズ。

## <a name="remarks"></a>Remarks

**/FILEALIGN**整列の倍数である境界上の出力ファイル内の各セクションをリンカーにオプション、*サイズ*値。 既定では、リンカーは、固定の配置のサイズを使用しません。

**/FILEALIGN**オプションは、ディスク使用率をより効率的に使用できますか、ページをディスクから読み込みます高速化します。 セクションのサイズを小さくはまたはのダウンロード サイズを小さく小型のデバイスで実行されるアプリの便利な可能性があります。 ディスク上のセクションの配置では、メモリ内の配置は影響しません。

出力ファイル内のセクションに関する情報を表示するには、[DUMPBIN](dumpbin-reference.md) を使用します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**コマンドライン**プロパティ ページで、**リンカー**フォルダー。

1. オプション名を入力 **/FILEALIGN:** およびサイズ、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)