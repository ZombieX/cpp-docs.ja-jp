---
title: -MACHINE (ターゲット プラットフォームの指定) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e159fe15b0aed441b1a96047a3ffb035077d6266
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708618"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (ターゲット プラットフォームの指定)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>Remarks

/MACHINE オプションは、プログラムのターゲット プラットフォームを指定します。

通常、/MACHINE オプションは指定する必要がありません。 LINK では、.obj ファイルからコンピューターの種類を推測するためです。 ただし、状況によっては、リンクかを判断できません、マシンの種類と問題を[リンカー ツール エラー LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md)します。 このようなエラー メッセージが出力された場合は、/MACHINE オプションを指定してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**詳細**プロパティ ページ。

1. 変更、**ターゲット マシン**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)