---
title: 致命的なエラー C1014 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1014
dev_langs:
- C++
helpviewer_keywords:
- C1014
ms.assetid: 4c01ef70-e765-4d07-a3fe-a11c19fb610b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c85cff5895326b9a96e9254cebb27fc267550f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103972"
---
# <a name="fatal-error-c1014"></a>致命的なエラー C1014

インクルード ファイルが多すぎます : 深さ = level

`#include` ディレクティブの入れ子が深すぎます。 入れ子になったディレクティブには、開いているファイルを含めることができます。 ディレクティブが含まれているソース ファイルは、1 つのファイルとしてカウントされます。