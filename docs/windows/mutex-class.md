---
title: Mutex クラス |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37aaafa636f43671eb18436a49490caa10cf349f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789307"
---
# <a name="mutex-class"></a>Mutex クラス

共有リソースを排他的に制御する同期オブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前       | 説明
---------- | ------------------------------------------------------
`SyncLock` | 同期ロックをサポートするクラスのシノニムです。

### <a name="public-constructor"></a>パブリック コンス トラクター

名前                   | 説明
---------------------- | ------------------------------------------------
[Mutex::mutex](#mutex) | `Mutex` クラスの新しいインスタンスを初期化します。

### <a name="public-members"></a>パブリック メンバー

名前                 | 説明
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::lock](#lock) | 現在のオブジェクトまでの待機、または`Mutex`リリース ミュー テックス、または指定されたタイムアウト期間が経過した、指定したハンドルに関連付けられているオブジェクト。

### <a name="public-operator"></a>パブリック演算子

名前                                 | 説明
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator =](#operator-assign) | 割り当て (移動)、指定した`Mutex`現在オブジェクト`Mutex`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`Mutex`

## <a name="requirements"></a>要件

**ヘッダー:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="lock"></a>Mutex::lock

現在のオブジェクトまでの待機、または`Mutex`リリース ミュー テックス、または指定されたタイムアウト期間が経過した、指定したハンドルに関連付けられているオブジェクト。

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>パラメーター

*(ミリ秒)*<br/>
タイムアウト間隔 (ミリ秒単位)。 既定値は、INFINITE で、無期限に待機します。

*h*<br/>
ハンドルを`Mutex`オブジェクト。

### <a name="return-value"></a>戻り値

## <a name="mutex"></a>Mutex::mutex

`Mutex` クラスの新しいインスタンスを初期化します。

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドル、または、ハンドルへの右辺値参照を`Mutex`オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンス トラクターの初期化を`Mutex`オブジェクト指定したハンドルから。 2 番目のコンス トラクターによって初期化、`Mutex`指定のハンドルとし、ミュー テックスの所有権を移動しますから、現在にオブジェクト`Mutex`オブジェクト。

## <a name="operator-assign"></a>Mutex::operator =

割り当て (移動)、指定した`Mutex`現在オブジェクト`Mutex`オブジェクト。

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
右辺値参照を`Mutex`オブジェクト。

### <a name="return-value"></a>戻り値

現在への参照を`Mutex`オブジェクト。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。、**移動セマンティクス**の[右辺値参照宣言子: & &](../cpp/rvalue-reference-declarator-amp-amp.md)します。
