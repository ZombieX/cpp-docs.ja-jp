---
title: '&lt;c&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <c>
dev_langs:
- C++
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74e2fdd2f970ca3c1f177dd8d7ea565757a03a4b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313001"
---
# <a name="ltcgt-visual-c"></a>&lt;c&gt; (Visual C++)

\<c> タグは、説明内のテキストをコードとしてマークすることを示します。 複数行をコードとして指定する場合は、[\<code>](../ide/code-visual-cpp.md) タグを使用します。

## <a name="syntax"></a>構文

```
<c>text</c>
```

#### <a name="parameters"></a>パラメーター

*テキスト*<br/>
コードとして示すテキストです。

## <a name="remarks"></a>コメント

コンパイル時に [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

```cpp
// xml_c_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_c_tag.xdc

/// Text for class MyClass.
class MyClass {
public:
   int m_i;
   MyClass() : m_i(0) {}

   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.
   /// </summary>
   int MyMethod(MyClass * a) {
      return a -> m_i;
   }
};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](../ide/xml-documentation-visual-cpp.md)