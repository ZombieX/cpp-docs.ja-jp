---
title: 共用体の格納 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 516de9411a91f4bb8dd5f8775544ef32e7863bb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038270"
---
# <a name="storage-of-unions"></a>共用体の格納

共用体変数に関連付けられたストレージは共用体の最大メンバーに必要なストレージです。 小さいメンバーが格納されると、共有体変数に未使用のメモリ領域が含まれる場合があります。 すべてのメンバーは、同じメモリ空間に格納され、同じアドレスで開始されます。 格納されている値は、値が別のメンバーに割り当てられるたびに上書きされます。 例:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

`x` 共有体のメンバーは、宣言の順番に、`char` 値へのポインター、`char` 値、**float** 値の配列です。 `x` に対して割り当てられたストレージは、`f` が共用体の最長メンバーであるため、20 要素の配列 `f` に必要なストレージです。 タグが共用体に関連付けられていないため、型は名前がないか "匿名" です。

## <a name="see-also"></a>参照

[共用体の宣言](../c-language/union-declarations.md)