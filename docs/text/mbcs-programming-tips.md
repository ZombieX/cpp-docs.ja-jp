---
title: MBCS のプログラミングについて |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac4ed378640942dbe33490d618cec7289125b0c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418789"
---
# <a name="mbcs-programming-tips"></a>MBCS のプログラミングについて

新しい開発では、エンド ユーザーに表示される可能性があるすべての文字列に Unicode 文字エンコーディングを使用することをお勧めします。 MBCS は、Unicode によって置き換えられたレガシ テクノロジです。 ここでは、MBCS を使用しており、Unicode への変換が実用的でない、既存のプログラムを保守する必要がある開発者のためのヒントを提供します。 ここで紹介するヒントは、MFC を使ったアプリケーションにも、使わないアプリケーションにも適用できます。 ここでは、次の内容について説明します。

- [MBCS プログラミングにおける一般的なアドバイス](../text/general-mbcs-programming-advice.md)

- [ポインターのインクリメントとデクリメント](../text/incrementing-and-decrementing-pointers.md)

- [バイト インデックス](../text/byte-indices.md)

- [文字列の最後の文字](../text/last-character-in-a-string.md)

- [文字の代入](../text/character-assignment.md)

- [文字の比較](../text/character-comparison.md)

- [バッファー オーバーフロー](../text/buffer-overflow.md)

## <a name="see-also"></a>関連項目

[マルチバイト文字セット (MBCS) のサポート](../text/support-for-multibyte-character-sets-mbcss.md)