---
title: CPtrList クラス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97eeeaaa2eea237eebda4f945f2c810268f406cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384963"
---
# <a name="cptrlist-class"></a>CPtrList クラス

void ポインターのリストをサポートします。

## <a name="syntax"></a>構文

```
class CPtrList : public CObject
```

## <a name="members"></a>メンバー

メンバー関数は、`CPtrList`クラスのメンバー関数のような[CObList](../../mfc/reference/coblist-class.md)します。 メンバー関数については `CObList` クラスの説明を参照してください。 任意の場所が表示、`CObject`関数パラメーターまたは戻り値としてのポインターへのポインターを置き換える**void**します。

`CObject*& CObList::GetHead() const;`

たとえば、次のように変換します。

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Remarks

`CPtrList` 実行時の型へのアクセスとダンプをサポートするために IMPLEMENT_DYNAMIC マクロが組み込まれています、`CDumpContext`オブジェクト。 ポインター リストの各要素をダンプする必要があるときは、ダンプ コンテキストの深さを 1 以上に設定する必要があります。

ポインター リストはシリアル化できません。

`CPtrList` オブジェクトが削除されたとき、またはその要素が削除されたときは、ポインターだけが削除されます。ポインターが参照するエンティティは削除されません。

使用しての詳細については`CPtrList`、記事をご覧ください[コレクション](../../mfc/collections.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>要件

**ヘッダー:** afxcoll.h

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CObList クラス](../../mfc/reference/coblist-class.md)
