---
title: リソース コンパイラの致命的なエラー RC1052 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1052
dev_langs:
- C++
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef276bdecf675a178f43f22e3aef88f4ed1c73cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071186"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>リソース コンパイラの致命的なエラー RC1052

コンパイラの制限: #if または #ifdef ブロックの入れ子のレベルが深すぎます。

プログラムが `#if` と `#ifdef` のディレクティブに許容される最大の入れ子レベルを超えました。

このエラーは、これらのプリプロセッサ ディレクティブを使用するインクルード ファイルによって発生することがあります。

この問題を解決するには、リソース ファイル内の、入れ子になっている `#if` と `#ifdef` ディレクティブの数を減らします。 リソース ファイルに含まれているヘッダー ファイルによって問題が発生している場合は、ヘッダー ファイル内の、入れ子になった `#if` と `#ifdef`ディレクティブの数を減らします。 これができない場合は、既存のヘッダー ファイルに対してプリプロセッサを実行して、新しいヘッダー ファイルを作成し、リソース ファイルに含めることを検討してください。 詳細については、次を参照してください。、 [/P (ファイルへのプリプロセス)](../../build/reference/p-preprocess-to-a-file.md)コンパイラ オプション。