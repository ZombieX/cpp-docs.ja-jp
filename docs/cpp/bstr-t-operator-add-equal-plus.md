---
title: _bstr_t::operator + =、+ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a440e8b8d078c7849de2a0b29f1d50b140d70070
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044770"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=、+

**Microsoft 固有の仕様**

`_bstr_t` オブジェクトの末尾に文字を追加するか、2 つの文字列を連結します。

## <a name="syntax"></a>構文

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>パラメーター

*s1*<br/>
`_bstr_t` オブジェクト。

*s2*<br/>
マルチバイト文字列。

*s3*<br/>
Unicode 文字列。

## <a name="remarks"></a>Remarks

これらの演算子は文字列連結を実行します。

- **operator + = (***s1***)** でカプセル化された文字を追加します`BSTR`の*s1*このオブジェクトのカプセル化されたの末尾に`BSTR`.

- **operator + (***s1***)** 新しい返します`_bstr_t`このオブジェクトの連結することによって作成される`BSTR`の*s1*します。

- **operator + (***s2***&#124;***s1***)** 新しいを返します`_bstr_t`を連結することによって作成される、マルチバイト文字列*s2*Unicode に変換されたで、`BSTR`にカプセル化*s1*します。

- **operator + (***s3* **、***s1***)** 新しいを返します`_bstr_t`Unicode 文字列を連結して作成されます。*s3*で、`BSTR`にカプセル化*s1*します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_bstr_t クラス](../cpp/bstr-t-class.md)