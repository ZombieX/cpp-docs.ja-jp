---
title: add_pointer クラス | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5f352f684818009210b4d394f4a820159da053
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101951"
---
# <a name="addpointer-class"></a>add_pointer クラス

指定された型から型へのポインターを作成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
変更する型。

## <a name="remarks"></a>Remarks

メンバー **typedef** `type`と同じ型の名前を付けます`remove_reference<T>::type*`します。 エイリアス`add_pointer_t`メンバーにアクセスするショートカット**typedef** `type`します。

参照からポインターを作成することは無効であるため、`add_pointer` は型へのポインターを作成する前に、指定された型から参照を削除します (存在する場合)。 その結果、型が参照であるかどうかを気にすることなく、型を `add_pointer` で使用できます。

## <a name="example"></a>例

次の例では、型の `add_pointer` がその型へのポインターと同じであることを示します。

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>要件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer クラス](../standard-library/remove-pointer-class.md)<br/>
