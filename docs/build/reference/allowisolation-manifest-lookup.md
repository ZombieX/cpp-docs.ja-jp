---
title: -ALLOWISOLATION (マニフェスト検索) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9197e67e46932f08a266258c41dab7922af2900
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318981"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (マニフェスト検索)

マニフェスト検索の動作を指定します。

## <a name="syntax"></a>構文

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Remarks

**/ALLOWISOLATION:NO**マニフェストがないかのように Dll を読み込むことを示します。 リンカーを設定すると、 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 、オプションのヘッダー内のビット`DllCharacteristics`フィールド。

**/ALLOWISOLATION**により、オペレーティング システムはマニフェストの検索と読み込みをします。

**/ALLOWISOLATION**既定値です。

実行可能ファイルの分離を無効にする、Windows ローダーは、アプリケーション マニフェストを新しく作成されたプロセスを検索する試行しません。 新しいプロセスがない既定のアクティベーション コンテキスト内で実行可能ファイルまたは名前の実行可能ファイルと同じディレクトリに配置マニフェストがある場合でも<em>実行可能ファイル名</em>**. exe.manifest**します。

詳細については、次を参照してください。 [Manifest Files Reference](/windows/desktop/SbsCs/manifest-files-reference)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **マニフェスト ファイル**プロパティ ページ。

1. 変更、**分離の許可**プロパティ。

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)
