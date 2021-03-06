---
title: C ランタイム エラー R6016 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b14d6e20f58ef5a9fbda6d640f5c8a596635d70c
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861708"
---
# <a name="c-runtime-error-r6016"></a>C ランタイム エラー R6016

not enough space for thread data

> [!NOTE]
> アプリの実行中にこのエラー メッセージが発生した場合、アプリがシャット ダウン、内部メモリの問題があるためです。 このエラーは、多くの理由が考えられますが、多くの場合、またはアドインまたはアプリで使用される拡張機能のバグによって、非常に低いメモリ条件をアプリでのバグによって原因が。
>
> このエラーを解決するには、次の手順を試してみます。
>
> - その他の実行中のアプリケーションを閉じるか、メモリを解放するため、コンピューターを再起動します。
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **を修復またはアプリを再インストールします。
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネル**削除、修復、またはアドインやアプリによって使用される拡張機能を再インストールします。
> - 確認**Windows Update**で、**コントロール パネルの **ソフトウェアの更新。
> - アプリの更新バージョンを確認します。 問題が解決しない場合は、アプリのベンダーにお問い合わせください。

**プログラマのための情報**

プログラムからオペレーティング システムが完了するのに十分なメモリを受信しなかったために、このエラーが発生します、 [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)または`_beginthreadex`呼び出し、またはスレッドでローカル ストレージが初期化されていない`_beginthread`または`_beginthreadex`します。

新規スレッドの開始時、ライブラリは、そのスレッド用に新しい内部データベースを生成する必要があります。 オペレーティング システムのメモリを使用してデータベースを展開できないと、スレッドは開始されず、スレッドの呼び出しプロセスは停止します。 これは、プロセスによって作成されたスレッドが多すぎる場合、またはスレッド ローカル ストレージが不足している場合に発生する可能性があります。

C ランタイム ライブラリ (CRT) を呼び出す実行可能ファイルを使用することをお勧めします。 `_beginthreadex` Windows API ではなく、スレッド作成用`CreateThread`します。 `_beginthreadex` は、スレッド ローカル ストレージで多くの CRT 関数によって使用される内部静的ストレージを初期化します。 `CreateThread` を使用してスレッドを作成すると、初期化された静的内部ストレージを必要とする CRT 関数が呼び出されたときに、R6016 でプロセスが終了する場合があります。