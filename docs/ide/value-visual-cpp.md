---
title: '&lt;value&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- value
- <value>
dev_langs:
- C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bd811080e3a5587056d67a45fce345b0a2b4d37
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419803"
---
# <a name="ltvaluegt-visual-c"></a>&lt;value&gt; (Visual C++)

\<value> タグでは、プロパティとプロパティ アクセサー メソッドを記述することができます。 Visual Studio 統合開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](../ide/summary-visual-cpp.md) タグが追加されることに注意してください。 その後、手動で \<value> タグを追加してプロパティが表す値を記述する必要があります。

## <a name="syntax"></a>構文

```
<value>property-description</value>
```

#### <a name="parameters"></a>パラメーター

*property-description*<br/>
プロパティの説明。

## <a name="remarks"></a>コメント

コンパイル時に [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

```
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](../ide/xml-documentation-visual-cpp.md)