---
title: スレッド処理モデルとクリティカル セクションのクラス (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b87fdac5220ede47f1acf19088e952fde408a413
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755958"
---
# <a name="threading-models-and-critical-sections-classes"></a>スレッド処理モデルとクリティカル セクションのクラス

次のクラス定義のスレッド処理モデルとクリティカル セクション。

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md)スレッド プール、アパートメント モデルの COM サーバーを実装します。

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md)スレッド プール、アパートメント モデルの COM サーバーを実装するためのメソッドを提供します。

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md)変数をインクリメントおよびデクリメントのスレッド セーフであるメソッドを提供します。 クリティカル セクションを提供します。

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md)変数をインクリメントおよびデクリメントのスレッド セーフであるメソッドを提供します。 クリティカル セクションは提供されません。

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md)変数をインクリメントおよびデクリメントするためのメソッドを提供します。 クリティカル セクションは提供されません。

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) 1 つのオブジェクト クラスの適切なスレッド モデル クラスを決定します。

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel)グローバルに利用可能であるオブジェクトの適切なスレッド モデル クラスを決定します。

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md)取得およびクリティカル セクションを解放するためのメソッドが含まれています。 クリティカル セクションが自動的に初期化します。

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md)取得およびクリティカル セクションを解放するためのメソッドが含まれています。 クリティカル セクションを明示的に初期化する必要があります。

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md)内のメソッドをミラー化`CComCriticalSection`せず、クリティカル セクション。 メソッドは、`CComFakeCriticalSection`何もしません。

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) CRT スレッドの作成機能を提供します。 スレッドの CRT 関数が使用する場合は、このクラスを使用します。

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) Windows スレッドの作成機能を提供します。 スレッドの CRT 関数を使用しない場合は、このクラスを使用します。

## <a name="see-also"></a>関連項目

[クラスの概要](../atl/atl-class-overview.md)

