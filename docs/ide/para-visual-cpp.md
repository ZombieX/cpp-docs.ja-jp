---
title: '&lt;para&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <para>
- para
dev_langs:
- C++
helpviewer_keywords:
- <para> C++ XML tag
- para C++ XML tag
ms.assetid: 35f2a1b3-bc14-4f13-bcb0-c39ccbf74d59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c36388e34b2f1e3cdc4d5664c014463c727e8369
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385093"
---
# <a name="ltparagt-visual-c"></a>&lt;para&gt; (Visual C++)

\<para> タグは、[\<summary>](../ide/summary-visual-cpp.md)、[\<remarks>](../ide/remarks-visual-cpp.md)、または [\<returns>](../ide/returns-visual-cpp.md) などのタグ内で使用し、テキストに構造を追加することができます。

## <a name="syntax"></a>構文

```
<para>content</para>
```

#### <a name="parameters"></a>パラメーター

*content*<br/>
段落のテキストです。

## <a name="remarks"></a>コメント

コンパイル時に [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

\<para> の使用例については、「[\<summary>](../ide/summary-visual-cpp.md)」を参照してください。

## <a name="see-also"></a>参照

[XML に関するドキュメント](../ide/xml-documentation-visual-cpp.md)