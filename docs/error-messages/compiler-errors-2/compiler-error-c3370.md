---
title: コンパイラ エラー C3370 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3370
dev_langs:
- C++
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dfd3ed72e379af754af53422842f88911916a79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135816"
---
# <a name="compiler-error-c3370"></a>コンパイラ エラー C3370

'idl_module name': 未定義の idl_module

[idl_module](../../windows/idl-module.md) を使用して DLL 内でエントリ ポイントを指定するには、まず `idl_module` を使用して DLL 名を指定する必要があります。

次の例では C3370 が生成されます。

```
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```