---
title: Module::genericreleasenotifier クラス |Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad7081e22762409682250da0330575885378e8ab
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161880"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier クラス

現在のモジュールの最後のオブジェクトがリリースされたときに、イベント ハンドラーを呼び出します。 イベント ハンドラーは、ラムダをファンクター、または関数へのポインターによって指定されます。

## <a name="syntax"></a>構文

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
イベント ハンドラーの場所を含むデータ メンバーの型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                                                                     | 説明
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | `Module::GenericReleaseNotifier` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                                                                     | 説明
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::genericreleasenotifier:: 呼び出し](#genericreleasenotifier-invoke) | 現在関連付けられているイベント ハンドラーを呼び出す`Module::GenericReleaseNotifier`オブジェクト。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                                                                          | 説明
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | ラムダ、ファンクター、または現在に関連付けられている関数へのポインター イベント ハンドラーを保持`Module::GenericReleaseNotifier`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>要件

**ヘッダー:** module.h

**名前空間:** Microsoft::WRL

## <a name="genericreleasenotifier-callback"></a>Module::GenericReleaseNotifier::callback_

ラムダ、ファンクター、または現在に関連付けられている関数へのポインター イベント ハンドラーを保持`Module::GenericReleaseNotifier`オブジェクト。

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier

`Module::GenericReleaseNotifier` クラスの新しいインスタンスを初期化します。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>パラメーター

*コールバック*<br/>
ラムダをファンクター、またはかっこ関数の演算子を呼び出すことができる関数へのポインター イベント ハンドラー (`()`)。

*release*<br/>
指定**true** 、基になる呼び出しを有効にする[モジュール:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md)メソッド。 それ以外の場合、指定**false**します。

## <a name="genericreleasenotifier-invoke"></a>Module::genericreleasenotifier:: 呼び出し

現在関連付けられているイベント ハンドラーを呼び出す`Module::GenericReleaseNotifier`オブジェクト。

```cpp
void Invoke();
```
