---
title: Idispeventsimpleimpl の使用 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 635edd00fbb7126b9d4d87615321387867b2978c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063199"
---
# <a name="using-idispeventsimpleimpl"></a>Idispeventsimpleimpl の使用

使用する場合`IDispEventSimpleImpl`イベントを処理する必要があります。

- クラスを派生[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)します。

- クラスにイベント シンク マップを追加します。

- 定義[_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md)のイベントを表す構造体。

- イベント シンク マップを使用するエントリを追加、 [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info)マクロ。

- 処理したいメソッドを実装します。

- イベント ソースをアドバイズことをお勧めします.

## <a name="example"></a>例

次の例は、処理する方法を示します、`DocumentChange`によって Word のイベントが発生した**アプリケーション**オブジェクト。 このイベントは、メソッドとしてで定義されている、`ApplicationEvents`ディスパッチ インターフェイス。

例は、[コード](../visual-cpp-samples.md)します。

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

この例では`#import`Word のタイプ ライブラリから必要なヘッダー ファイルを生成します。 Word の他のバージョンでこの例を使用する場合は、正しい mso dll ファイルを指定する必要があります。 たとえば、Office 2000 mso9.dll を提供し、OfficeXP が mso.dll を提供します。 このコードは、stdafx.h から簡素化します。

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

この例では実際に使用されるタイプ ライブラリからの唯一の情報は、Word の CLSID`Application`オブジェクトとの IID、`ApplicationEvents`インターフェイス。 この情報はコンパイル時にのみ使用します。

Simple.h に次のコードが表示されます。 関連するコードは、コメントでされています。

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

次のコードは Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>関連項目

[イベント処理](../atl/event-handling-and-atl.md)<br/>
[コード](../visual-cpp-samples.md)

