---
title: task_handle クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
dev_langs:
- C++
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a1effbd833ec28da2285d3c38fb58ee5ce7928
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388421"
---
# <a name="taskhandle-class"></a>task_handle クラス

`task_handle` クラスは個々の並列作業項目を表します。 このクラスは、1 つの処理を実行するために必要な命令およびデータをカプセル化します。

## <a name="syntax"></a>構文

```
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

#### <a name="parameters"></a>パラメーター

*_Function*<br/>
によって表される作業を実行するときに呼び出される関数オブジェクトの種類、`task_handle`オブジェクト。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[task_handle](#ctor)|新しい `task_handle` オブジェクトを構築します。 タスクの作業は、コンス トラクターにパラメーターとして指定された関数を呼び出すことによって実行されます。|
|[~ task_handle デストラクター](#dtor)|`task_handle` オブジェクトを破棄します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|タスク ハンドルの作業を実行するために、ランタイムが呼び出す関数呼び出し演算子。|

## <a name="remarks"></a>Remarks

`task_handle` オブジェクトを組み合わせて使用することができます、`structured_task_group`またはより一般的な`task_group`処理の並列タスクを分解するオブジェクト。 詳細については、次を参照してください。[タスクの並列化](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)します。

注意の作成者、`task_handle`オブジェクトは、作成の有効期間の保守を担当`task_handle`まで、これは、同時実行ランタイムで不要になったオブジェクトします。 通常、これは、`task_handle`オブジェクトをする必要がありますいないまで消滅させるため、`wait`または`run_and_wait`のメソッド、`task_group`または`structured_task_group`これがキューに入れるが呼び出されました。

`task_handle` オブジェクトは通常、C++ ラムダと組み合わせて使用されます。 、ラムダ式の実際の型がわからないため、 [make_task](concurrency-namespace-functions.md#make_task)関数が通常作成に使用する`task_handle`オブジェクト。

ランタイムに渡す処理関数のコピーを作成する、`task_handle`オブジェクト。 そのため、関数で発生する状態の変更はオブジェクトに渡すこと、`task_handle`オブジェクトは、その関数のオブジェクトのコピーには表示されません。

## <a name="inheritance-hierarchy"></a>継承階層

`task_handle`

## <a name="requirements"></a>要件

**ヘッダー:** ppl.h

**名前空間:** concurrency

##  <a name="task_handle__operator_call"></a> operator()

タスク ハンドルの作業を実行するために、ランタイムが呼び出す関数呼び出し演算子。

```
void operator()() const;

```

##  <a name="task_handle__ctor"></a> task_handle

新しい `task_handle` オブジェクトを構築します。 タスクの作業は、コンス トラクターにパラメーターとして指定された関数を呼び出すことによって実行されます。

```
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>パラメーター

*_Func*<br/>
によって表される作業を実行するときに呼び出される関数、`task_handle`オブジェクト。 ラムダをファンクター、関数へのポインターがありますまたはシグネチャを持つ関数呼び出し演算子のバージョンをサポートする任意のオブジェクト`void operator()()`します。

### <a name="remarks"></a>Remarks

ランタイムは、コンス トラクターに渡す処理関数のコピーを作成します。 そのため、関数で発生する状態の変更はオブジェクトに渡すこと、`task_handle`オブジェクトは、その関数のオブジェクトのコピーには表示されません。

##  <a name="dtor"></a> ~task_handle

`task_handle` オブジェクトを破棄します。

```
~task_handle();
```

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[task_group クラス](task-group-class.md)<br/>
[structured_task_group クラス](structured-task-group-class.md)
