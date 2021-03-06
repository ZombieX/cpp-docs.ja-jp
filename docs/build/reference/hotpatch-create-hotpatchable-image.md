---
title: -hotpatch (ホットパッチ可能なイメージの作成) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97e1b6197ea60099457db7788ad7e24b96c9fcb8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716977"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (ホットパッチ可能なイメージの作成)

イメージをホットパッチできるようにします。

## <a name="syntax"></a>構文

```
/hotpatch
```

## <a name="remarks"></a>Remarks

ときに **/hotpatch**されるコンパイルで、コンパイラは、各関数の最初の命令が、ホットパッチに必要な 2 バイト以上であること。

使用した後、イメージのホットパッチを行うための準備を完了する **/hotpatch**使用する必要がありますをコンパイルする[/FUNCTIONPADMIN (ホットパッチ可能なイメージの作成)](../../build/reference/functionpadmin-create-hotpatchable-image.md)にリンクします。 コンパイルし、cl.exe の 1 つの呼び出しを使用して、イメージを関連付ける **/hotpatch**意味 **/functionpadmin**します。

手順については、常に 2 バイトであるため、ARM アーキテクチャでより大きいまたは、x64 コンパイルは常に扱われます場合と **/hotpatch**指定されているを指定する必要はありません **/hotpatch**ときにこれらのターゲットのコンパイルします。ただし、するを使用してリンクする必要がありますも **/functionpadmin**にそれらのホットパッチ可能なイメージを作成します。 **/Hotpatch**コンパイラ オプションのみに影響を与えます x86 コンパイルします。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. コンパイラ オプションを追加、**追加オプション**ボックス。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="guidance"></a>ガイダンス

更新プログラム管理に関する詳細についてを参照してください「管理用の更新のセキュリティ ガイダンス」 [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx)します。

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)