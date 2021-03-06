---
title: -CLRTHREADATTRIBUTE (CLR スレッド属性の設定) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea5b75c9f0691ef74c35ed405d64fc3389c4fcd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705797"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (CLR スレッド属性の設定)

CLR プログラムのエントリ ポイントにスレッド属性を明示的に指定します。

## <a name="syntax"></a>構文

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>パラメーター

**MTA**<br/>
MTAThreadAttribute 属性をプログラムのエントリ ポイントに適用されます。

**[なし]**<br/>
/CLRTHREADATTRIBUTE を指定しないと同じです。  既定のスレッド属性を設定する共通言語ランタイム (CLR) を使用できます。

**STA**<br/>
STAThreadAttribute 属性をプログラムのエントリ ポイントに適用されます。

## <a name="remarks"></a>Remarks

スレッド属性設定のみ有効です、.exe を構築するときに、メイン スレッドのエントリ ポイントに影響するため。

使用する場合は、(main または wmain の例では、)、既定のエントリ ポイント指定スレッド処理モデルを/CLRTHREADATTRIBUTE を使用するかまたは配置することで、スレッド処理属性 (STAThreadAttribute または MTAThreadAttribute) を既定のエントリ関数。

既定以外のエントリ ポイントを使用する場合は、/CLRTHREADATTRIBUTE を使用するか、スレッドを配置することで、既定以外のエントリ関数で属性し、既定以外のエントリ ポイントを指定し、スレッド処理モデルを指定[/ENTRY](../../build/reference/entry-entry-point-symbol.md).

ソース コードで指定されたスレッド処理モデルは、/CLRTHREADATTRIBUTE で指定されたスレッド モデルと一致しません、リンカーは/CLRTHREADATTRIBUTE を無視し、ソース コードで指定されたスレッド処理モデルを適用します。

CLR プログラムは、シングル スレッドを使用する COM オブジェクトをホストしている場合は、シングル スレッドを使用するために必要になります。  マルチ スレッドを使用する CLR プログラム場合、シングル スレッドを使用する COM オブジェクトをホストできません。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[構成プロパティ]** ノードを展開します。

1. 展開、**リンカー**ノード。

1. 選択、**詳細**プロパティ ページ。

1. 変更、 **CLR スレッド属性の**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)