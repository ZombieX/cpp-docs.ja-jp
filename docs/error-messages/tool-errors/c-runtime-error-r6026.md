---
title: C ランタイム エラー R6026 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6026
dev_langs:
- C++
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b10075912ce4fde65699cf7b2d413c0bdd10f0
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860798"
---
# <a name="c-runtime-error-r6026"></a>C ランタイム エラー R6026

stdio 初期化領域が足りません。

> [!NOTE]
> アプリの実行中にこのエラー メッセージが発生した場合、アプリがシャット ダウン、内部メモリの問題があるためです。 このエラーは、いくつかの理由がありますが、通常原因が、非常に低いメモリ条件。 アプリでのバグを使用する Visual C ライブラリの破損またはドライバーにも発生することができます。
>
> このエラーを解決するには、次の手順を試してみます。
>
> - その他の実行中のアプリケーションを閉じるか、メモリを解放するため、コンピューターを再起動します。
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **を修復またはプログラムを再インストールします。
> - 別のアプリまたはドライバーの最新のインストール前に、アプリが動作している場合は、使用、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **を削除する、新しいアプリまたはドライバー、およびアプリをもう一度やり直してください。
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **修復または Microsoft Visual C Redistributable のすべてのコピーを再インストールします。
> - 確認**Windows Update**で、**コントロール パネルの **ソフトウェアの更新。
> - アプリの更新バージョンを確認します。 問題が解決しない場合は、アプリのベンダーにお問い合わせください。

**プログラマのための情報**

このエラーは、C ランタイムで標準の I/O のサポートを初期化するために使用できる十分な空きメモリがない場合に発生します。 このエラーは、アプリの起動時に通常発生します。 アプリとドライバーと dll を読み込むことが起動時に、ヒープを破損しないことを確認します。