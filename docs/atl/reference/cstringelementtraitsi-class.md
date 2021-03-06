---
title: CStringElementTraitsI クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29df4bd550a5de232b5ced0510e8dbfc68e59d42
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060755"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI クラス

このクラスは、コレクション クラスのオブジェクトに格納された文字列に関連する静的関数を提供します。 似ています[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)が小文字の比較を実行します。

## <a name="syntax"></a>構文

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|コレクション クラスのオブジェクトに要素を追加するために使用するデータ型。|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|コレクション クラスのオブジェクトから要素を取得するために使用するデータ型。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|2 つの文字列要素の場合の相違を無視して等しいかどうかを比較する、この静的関数を呼び出します。|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|ケースの相違を無視して、2 つの文字列要素を比較する、この静的関数を呼び出します。|
|[CStringElementTraitsI::Hash](#hash)|指定した文字列の要素のハッシュ値を計算する、この静的関数を呼び出します。|

## <a name="remarks"></a>Remarks

このクラスは、文字列を比較し、ハッシュ値を作成するために、静的関数を提供します。 これらの関数は、文字列ベースのデータを格納するコレクション クラスを使用する場合に便利です。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)文字列オブジェクトを処理する参照として処理されます。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements

2 つの文字列要素の場合の相違を無視して等しいかどうかを比較する、この静的関数を呼び出します。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の要素を文字列します。

*str2*<br/>
2 番目の文字列要素。

### <a name="return-value"></a>戻り値

要素が false でそれ以外の場合、等しい場合は true を返します。

### <a name="remarks"></a>Remarks

比較では大文字と小文字を区別しません。

##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered

ケースの相違を無視して、2 つの文字列要素を比較する、この静的関数を呼び出します。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の要素を文字列します。

*str2*<br/>
2 番目の文字列要素。

### <a name="return-value"></a>戻り値

< 0、0 の文字列が一致している場合場合*str1*がより小さい*str2*、または > 0 場合*str1*がより大きい*str2*します。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)メソッドは、比較を実行するために使用します。

### <a name="remarks"></a>Remarks

比較では大文字と小文字を区別しません。

##  <a name="hash"></a>  CStringElementTraitsI::Hash

指定した文字列の要素のハッシュ値を計算する、この静的関数を呼び出します。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>パラメーター

*str*<br/>
文字列の要素。

### <a name="return-value"></a>戻り値

文字列の内容を使用して計算されたハッシュ値を返します。

##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE

コレクション クラスのオブジェクトに要素を追加するために使用するデータ型。

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE

コレクション クラスのオブジェクトから要素を取得するために使用するデータ型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>関連項目

[CElementTraitsBase クラス](../../atl/reference/celementtraitsbase-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits クラス](../../atl/reference/cstringelementtraits-class.md)
