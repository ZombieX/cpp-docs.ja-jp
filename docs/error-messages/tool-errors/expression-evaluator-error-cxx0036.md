---
title: 式エバリュエーター エラー CXX0036 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94ed846d2d4ebda2e457ee772a9f8bf081d69d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077173"
---
# <a name="expression-evaluator-error-cxx0036"></a>式エバリュエーター エラー CXX0036

コンテキストが正しくありません {...} specification

このメッセージは、コンテキスト演算子の使用中のいくつかのエラーのいずれかで生成されることができます (**{}**)。

- コンテキスト演算子の構文 (**{}**) 指定されました。

   コンテキスト演算子の構文です。

     {*関数*、*モジュール*、*dll*}*式*

   コンテキストを指定しますこの*式*します。 コンテキスト演算子は、型キャストと同じ優先順位と使用状況が。

   末尾のコンマは省略できます。 いずれか*関数*、*モジュール*、または*dll*リテラルのコンマを含む名前全体をかっこで囲む必要があります。

- 関数名の綴りが間違って、または、指定されたモジュールまたはダイナミック リンク ライブラリに存在しません。

   C は大文字小文字を区別する言語のため*関数*ソースで定義されている大文字小文字の区別で指定する必要があります。

- モジュールまたは DLL が見つかりませんでした。

   指定されたモジュールまたは DLL の完全なパス名を確認します。

このエラーは、can0036 と同じものと同じです。