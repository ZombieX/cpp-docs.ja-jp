---
title: コンパイラ エラー C3118 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3118
dev_langs:
- C++
helpviewer_keywords:
- C3118
ms.assetid: 40fbe681-8868-4cb2-a2b2-4db4449319a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 320d92bd97e3b5f9bb696959ee25ca33cba3544a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063425"
---
# <a name="compiler-error-c3118"></a>コンパイラ エラー C3118

'interface': インターフェイスは仮想継承をサポートしていません

仮想インターフェイスから継承しようとしました。 たとえば、オブジェクトに適用された

```
// C3118.cpp
__interface I1 {
};

__interface I2 : virtual I1 {   // C3118
};
```

このエラーを生成します。