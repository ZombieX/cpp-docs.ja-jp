---
title: bad_target クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b13aecabbf7f9935671b6bd44b654e78c5cd58dd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395077"
---
# <a name="badtarget-class"></a>bad_target クラス

このクラスは、実行する操作の無効なターゲットへのポインターがメッセージング ブロックに渡された場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```
class bad_target : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[bad_target](#ctor)|オーバーロードされます。 `bad_target` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

など、別のターゲットで予約されているメッセージを使用しようとしています。 保持しない予約を解放したり、ターゲット上の理由からは、通常この例外がスローされます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`bad_target`

## <a name="requirements"></a>要件

**ヘッダー:** concrt.h

**名前空間:** concurrency

##  <a name="ctor"></a> bad_target

`bad_target` オブジェクトを構築します。

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>パラメーター

*メッセージ (_m)*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[非同期メッセージ ブロック](../../../parallel/concrt/asynchronous-message-blocks.md)

