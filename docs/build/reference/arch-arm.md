---
title: -arch (ARM) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfa68eece4a7fd626c787fd5421d9dcac58cf805
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435469"
---
# <a name="arch-arm"></a>/arch (ARM)

ARM でのコード生成のアーキテクチャを指定します。 参照してください[/arch (x86)](../../build/reference/arch-x86.md)と[/arch (x64)](../../build/reference/arch-x64.md)します。

## <a name="syntax"></a>構文

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>引数

**/arch:ARMv7VE**<br/>
ARMv7VE 仮想化拡張命令の使用を有効にします。

**/arch:VFPv4**<br/>
ARM VFPv4 命令の使用を有効にします。 このオプションを指定しない場合は、VFPv3 が既定値です。

## <a name="remarks"></a>Remarks

`_M_ARM_FP` (ARM のみ) 用のマクロを示します。 存在する場合、 **/arch**コンパイラ オプションを使用します。 詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。

使用すると[/clr](../../build/reference/clr-common-language-runtime-compilation.md)をコンパイルする **/arch**マネージ関数のコード生成に影響を与えません。 **/arch**だけでネイティブ関数の生成のコードに影響します。

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Visual Studio で、/arch:ARMv7VE または/arch:VFPv4 コンパイラ オプションを設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、「[プロジェクト プロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加`/arch:ARMv7VE`または`/arch:VFPv4`します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>

## <a name="see-also"></a>関連項目

[/arch (最小限の CPU アーキテクチャ)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)