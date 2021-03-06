---
title: Platform::mtathreadattribute クラス |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2bac4ae71d98cb81eaa05bd3fd6fdf817145e22
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163753"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute クラス

アプリケーションのスレッド モデルがマルチスレッド アパートメント (MTA) であることを示します。

## <a name="syntax"></a>構文

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[MTAThreadAttribute コンス トラクター 1](#ctor)コンス トラクター|クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

MTAThreadAttribute 属性が継承[platform::object Class](../cppcx/platform-object-class.md)します。 また MTAThreadAttribute は次のメンバーをオーバーロードしたり、含んだりします。

|名前|説明|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|このインスタンスのハッシュ コードを返します。|
|[MTAThreadAttribute::ToString](#tostring)|現在のオブジェクトを表す文字列を返します。|

## <a name="inheritance-hierarchy"></a>継承階層

`Platform`

### <a name="requirements"></a>要件

**メタデータ:** platform.winmd

**名前空間:** Platform

## <a name="ctor"></a> MTAThreadAttribute コンス トラクター

MTAThreadAttribute クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>パラメーター

*obj*<br/>
比較対象のオブジェクト。

### <a name="return-value"></a>戻り値

**true**オブジェクトが、それ以外の場合は**false**します。

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

このインスタンスのハッシュ コードを返します。

### <a name="syntax"></a>構文

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>戻り値

対象のインスタンスのハッシュ コード。

## <a name="tostring"></a> MTAThreadAttribute::ToString

現在のオブジェクトを表す文字列を返します。

### <a name="syntax"></a>構文

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>戻り値

現在のオブジェクトを表す文字列。

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)