---
title: uuid (C++ 属性) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3eddf1981aba8babcb87562ed546ce4086499fd7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071340"
---
# <a name="uuid-c-attributes"></a>uuid (C++ 属性)

クラスまたはインターフェイスの一意の ID を指定します。

## <a name="syntax"></a>構文

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>パラメーター

*uuid*<br/>
128 ビットの一意の識別子です。

## <a name="remarks"></a>Remarks

インターフェイスまたはクラスの定義が指定しないかどうか、 **uuid** C++ 属性に、その後、Visual C コンパイラはいずれかで提供されます。 指定した場合、 **uuid**引用符を含める必要があります。

指定しない場合**uuid**コンパイラが、マシン上の別の属性プロジェクトでのインターフェイスまたはクラスと同じ名前の同じ GUID を生成します。

Uuidgen.exe または Guidgen.exe を使用して、独自の一意の Id を生成することができます。 (これらのツールのいずれかを実行する をクリックして**開始** をクリック**実行**メニュー。 Enter、必要なツールの名前。)

ATL にも使用しないプロジェクトで使用する場合を指定する、 **uuid**属性が指定した場合と同じ、 [uuid](../../cpp/uuid-cpp.md) **_ _declspec**修飾子。 取得する、 **uuid**クラスを使用することができます[_ _uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>例

参照してください、[バインド可能な](bindable.md)の使用サンプルの例を**uuid**します。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**、**インターフェイス**、**共用体**、**列挙型**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/desktop/Midl/uuid)