---
title: auto_gcroot::operator auto_gcroot |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_gcroot.operator auto_gcroot
- auto_gcroot::operator auto_gcroot
- msclr.auto_gcroot.operator auto_gcroot
- msclr::auto_gcroot::operator auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot operator
ms.assetid: 43e3f27a-9f68-444f-9149-a9282a9b935a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dfe81532aa38e79e272e87489a635db66187109b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418217"
---
# <a name="autogcrootoperator-autogcroot"></a>auto_gcroot::operator auto_gcroot

型キャスト演算子間`auto_gcroot`と互換性のある型。

## <a name="syntax"></a>構文

```
template<typename _other_type>
operator auto_gcroot<_other_type>();
```

## <a name="return-value"></a>戻り値

現在`auto_gcroot`にキャスト`auto_gcroot<_other_type>`します。

## <a name="example"></a>例

```
// msl_auto_gcroot_op_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassB^> b = gcnew ClassB("first");
   b->PrintHello();
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="requirements"></a>要件

**ヘッダー ファイル** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>関連項目

[auto_gcroot のメンバー](../dotnet/auto-gcroot-members.md)