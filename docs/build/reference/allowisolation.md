---
title: -ALLOWISOLATION |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07414c86663ea6143a471691b01e584cdc033258
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392828"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

マニフェスト検索の動作を指定します。

## <a name="syntax"></a>構文

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Remarks

**/ALLOWISOLATION**により、オペレーティング システムはマニフェストの検索と読み込みをします。

**/ALLOWISOLATION**既定値です。

**/ALLOWISOLATION:NO**マニフェスト、およびエラーの原因がない場合に、実行可能ファイルが読み込まれていることを示します[EDITBIN リファレンス](../../build/reference/editbin-reference.md)を設定する、 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 、オプションのヘッダー内のビット`DllCharacteristics`フィールド。

実行可能ファイルの分離が無効の場合、Windows ローダーは、新しく作成されたプロセスに対応するアプリケーション マニフェストの検索を試行しません。 自体の実行可能ファイルにマニフェストがあるか、名前を持つ場合は、マニフェストがある場合でも、新しいプロセスは既定のアクティベーション コンテキストにない*実行可能ファイル名*。 exe.manifest します。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION (マニフェスト検索)](../../build/reference/allowisolation-manifest-lookup.md)<br/>
[マニフェスト ファイルのリファレンス](/windows/desktop/SbsCs/manifest-files-reference)