---
title: lock::operator! = |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock.operator!=
- msclr.lock.operator!=
- msclr::lock::operator!=
- lock::operator!=
dev_langs:
- C++
helpviewer_keywords:
- lock::operator!=
ms.assetid: ed1d674e-9ee9-4257-8a7e-2e3567d50222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6ea18e7881b3569a3f4f9da237dc8a2b31a2ef29
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163505"
---
# <a name="lockoperator"></a>lock::operator!=

非等値演算子。

## <a name="syntax"></a>構文

```
template<class T> bool operator!=(
   T t
);
```

#### <a name="parameters"></a>パラメーター

*t*<br/>
非等値を比較するオブジェクト。

## <a name="return-value"></a>戻り値

返します**true**場合`t`ロックのオブジェクトとは異なります**false**それ以外の場合。

## <a name="example"></a>例

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```

## <a name="requirements"></a>要件

**ヘッダー ファイル** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>関連項目

[lock のメンバー](../dotnet/lock-members.md)<br/>
[lock::operator==](../dotnet/lock-operator-equality.md)