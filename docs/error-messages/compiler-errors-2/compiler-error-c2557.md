---
title: コンパイラ エラー C2557 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2557
dev_langs:
- C++
helpviewer_keywords:
- C2557
ms.assetid: 48a33d82-aa16-4658-b346-2311fcb39864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f975bdacf4db0460f6b12cd4f340c72e50f01a8c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102607"
---
# <a name="compiler-error-c2557"></a>コンパイラ エラー C2557

'identifier': プライベート メンバー、プロテクト メンバーの初期化にはコンストラクターが必要です

プライベート メンバーまたはプロテクト メンバーに値を割り当てることができるのは、メンバーとフレンドのみです。 非パブリック メンバーは、クラス コンストラクターで初期化する必要があります。