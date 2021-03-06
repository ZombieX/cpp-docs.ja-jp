---
title: コンパイラの警告 (レベル 3) C4159 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4159
dev_langs:
- C++
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43e3d63ad1d482222c4ffa7aa7435d0e660f3985
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223319"
---
# <a name="compiler-warning-level-3-c4159"></a>コンパイラの警告 (レベル 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>プラグマ pragma(pop,...): 以前にプッシュされた識別子がポップ '*識別子*'

## <a name="remarks"></a>Remarks

ソース コードに含まれる、**プッシュ**プラグマの識別子で命令が続く、 **pop**識別子のない命令。 その結果、*識別子*の表示された場合は、以降の使用は、*識別子*予期しない動作が発生する可能性があります。

## <a name="example"></a>例

この警告を回避するで識別子を指定、 **pop**命令。 例えば:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```