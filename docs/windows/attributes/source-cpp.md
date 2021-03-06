---
title: ソース (C++ COM 属性) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7bc10b89df58dc72c35855fea43c2a0387f9efd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058467"
---
# <a name="source-c"></a>source (C++)

クラスの場合、接続ポイント用の COM オブジェクトのソース インターフェイスを指定します。 プロパティまたはメソッドでは、オブジェクトまたはイベントのソースをバリアントにメンバーを返すことを示します。

## <a name="syntax"></a>構文

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>パラメーター

*interfaces*<br/>
クラスに属性のソースを適用するときに指定する 1 つまたは複数のインターフェイス。 ソースは、プロパティやメソッドに適用されるときに、このパラメーターは使用されません。

## <a name="remarks"></a>Remarks

**ソース**C++ 属性と同じ機能を持つ、[ソース](/windows/desktop/Midl/source)MIDL 属性。

使用することができます、[既定](default-cpp.md)オブジェクトの既定のソース インターフェイスを指定する属性。

## <a name="example"></a>例

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**、**インターフェイス**|
|**反復可能**|いいえ|
|**必要な属性**|`coclass` (クラスまたは構造体に適用される) と|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[coclass](coclass.md)