---
title: コンパイラ エラー C3483 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: decc04f25689b24c560f59a71fd22a9708754352
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091687"
---
# <a name="compiler-error-c3483"></a>コンパイラ エラー C3483

'var' は既にラムダ キャプチャ リストに含まれています

ラムダ式のキャプチャ リストに同じ変数を複数回渡しました。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- キャプチャ リストから変数のすべての追加インスタンスを削除します。

## <a name="example"></a>例

次の例では、変数 `n` がラムダ式のキャプチャ リストに複数回出現するため、C3483 が生成されます。

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>関連項目

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)