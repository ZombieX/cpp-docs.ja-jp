---
title: is_const クラス | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_const
dev_langs:
- C++
helpviewer_keywords:
- is_const class
- is_const
ms.assetid: 55b8e887-9c3f-4a1d-823a-4a257337b205
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83c929548d95ec0a741fd4b65c372402d22f2679
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099552"
---
# <a name="isconst-class"></a>is_const クラス

型が const かどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_const;
```

### <a name="parameters"></a>パラメーター

*Ty*<br/>
照会する型。

## <a name="remarks"></a>Remarks

場合、型述語のインスタンスは true を保持*Ty*は`const-qualified`します。

## <a name="example"></a>例

```cpp
// std__type_traits__is_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
{
    int val;
};

int main()
{
    std::cout << "is_const<trivial> == " << std::boolalpha
        << std::is_const<trivial>::value << std::endl;
    std::cout << "is_const<const trivial> == " << std::boolalpha
        << std::is_const<const trivial>::value << std::endl;
    std::cout << "is_const<int> == " << std::boolalpha
        << std::is_const<int>::value << std::endl;
    std::cout << "is_const<const int> == " << std::boolalpha
        << std::is_const<const int>::value << std::endl;

    return (0);
}

```

```Output
is_const<trivial> == false
is_const<const trivial> == true
is_const<int> == false
is_const<const int> == true
```

## <a name="requirements"></a>要件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_volatile クラス](../standard-library/is-volatile-class.md)<br/>
