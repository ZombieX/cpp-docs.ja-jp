---
title: 一次式の文字列リテラル | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 818284a0eabce779d9f52e8fe7b3af4cc1d8df4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095529"
---
# <a name="string-literals-in-primary-expressions"></a>一次式の文字列リテラル

"文字列リテラル" は、二重引用符で囲まれた文字、ワイド文字、または隣接する文字のシーケンスです。 これらは変数ではないため、文字列リテラルおよびその要素はいずれも代入演算の左側のオペランドにはなりません。 文字列リテラルの型は `char` の配列 (またはワイド文字列リテラルを表す `wchar_t` の配列) です。 式に含まれる配列は、ポインターに変換されます。 文字列の詳細については、[文字列リテラル](../c-language/c-string-literals.md)に関するページをご覧ください。

## <a name="see-also"></a>参照

[C 一次式](../c-language/c-primary-expressions.md)