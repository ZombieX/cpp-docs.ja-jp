---
title: -PDB (プログラム データベースの使用) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs:
- C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8717be9ee8f754f4e61dbed0211360a0b4f4f780
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717243"
---
# <a name="pdb-use-program-database"></a>/PDB (プログラム データベースの使用)

```
/PDB:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
プログラム データベース (PDB)、リンカーによって作成されるユーザー指定の名前。 既定の名前が置き換えられます。

## <a name="remarks"></a>Remarks

既定では、ときに[/debug](../../build/reference/debug-generate-debug-info.md)を指定すると、リンカーはデバッグ情報を保持するプログラム データベース (PDB) を作成します。 PDB の既定のファイル名は、プログラムと拡張子 .pdb の基本の名前を持ちます。

/PDB を使用して:*filename* PDB ファイルの名前を指定します。 /DEBUG が指定されていない場合は、/PDB オプションは無視されます。

PDB ファイルには、最大 2 GB を指定できます。

詳細については、次を参照してください。[リンカー入力としての .pdb ファイル](../../build/reference/dot-pdb-files-as-linker-input.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**デバッグ**プロパティ ページ。

1. 変更、**プログラム データベース ファイルの生成**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)