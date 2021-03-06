---
title: strict_gs_check |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs:
- C++
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d78a4d249852b730d80054b62a06699f50356b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067278"
---
# <a name="strictgscheck"></a>strict_gs_check

このプラグマは、強化されたセキュリティ チェックを提供します。

## <a name="syntax"></a>構文

```
#pragma strict_gs_check([push,] on )
#pragma strict_gs_check([push,] off )
#pragma strict_gs_check(pop)
```

## <a name="remarks"></a>Remarks

コンパイラが関数スタックにランダム クッキーを挿入し、スタック ベースのバッファー オーバーランのカテゴリの検出に役立つように指示します。 既定で、 `/GS` (バッファー セキュリティ チェック) コンパイラ オプションがすべての関数に対してクッキーを挿入できません。 詳細については、「[/GS (バッファーのセキュリティ チェック)](../build/reference/gs-buffer-security-check.md)」を参照してください。

コンパイルする必要があります`/GS`(バッファー セキュリティ チェック) を有効にする**strict_gs_check**します。

このプラグマは、有害なデータに対して公開される可能性があるコード モジュールで使用してください。 このプラグマは非常に積極的です。この防御を必要としない可能性があり、ただし生成アプリケーションのパフォーマンスに対する影響を最小化するために最適化された関数に適用されます。

このプラグマを使用した場合でも、安全なコードを記述する必要があります。 つまり、コードにバッファー オーバーランがないことを確認します。 **strict_gs_check**アプリケーションをコード内で残るバッファー オーバーランから保護する場合があります。

## <a name="example"></a>例

次のコードでは、ローカル配列に配列をコピーすると、バッファー オーバーランが発生します。 このコードをコンパイルすると`/GS`配列のデータ型がポインターであるために、スタックでは、クッキーを挿入していません。 追加、 **strict_gs_check**プラグマが関数スタックにスタック クッキーを強制します。

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // *** This buffer is subject to being overrun!! ***
    void *pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>関連項目

[プラグマ ディレクティブと __Pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/GS (バッファーのセキュリティ チェック)](../build/reference/gs-buffer-security-check.md)