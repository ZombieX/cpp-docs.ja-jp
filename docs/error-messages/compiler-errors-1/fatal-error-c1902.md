---
title: 致命的なエラー C1902 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5a443b5f80eabe9691cf8ff5220bb9b66da51e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052570"
---
# <a name="fatal-error-c1902"></a>致命的なエラー C1902

プログラム データベース マネージャーが一致しません。インストールを確認してください。

プログラム データベース ファイル (.pdb) は、新しいバージョンの mspdb を使用して作成された*XXX*.dll、システムで、コンパイラが検出されたものです。 このエラーは mspdbsrv.exe または mspdbcore.dll が見つからないか、mspdb は異なるバージョンがあることには、通常を示します*XXX*.dll です。 (、 *XXX* 、mspdb 内のプレース ホルダー*XXX*製品リリースごとに .dll ファイル名の変更。 たとえば、Visual Studio 2015 で、ファイル名は mspdb140.dll。)

Mspdbsrv.exe、mspdbcore.dll、mspdb の一致するバージョンを確認します。*XXX*.dll は、システムにインストールされます。 バージョンが一致しないが、ターゲット プラットフォームのコンパイラとリンク ツールを含むディレクトリにコピーされていないことを確認します。 たとえば、する可能性がありますファイルをコピー、設定がない場合、コマンド プロンプトから、コンパイラまたはリンク ツールを起動できるように、**パス**環境変数それに応じて。