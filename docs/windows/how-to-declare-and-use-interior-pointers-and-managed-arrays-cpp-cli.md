---
title: '方法: 内部ポインターおよびマネージ配列宣言および使用 (C +/cli CLI) |Microsoft Docs'
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a18170d66ef2b2fe374085557d7fca4411c48ec6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080625"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>方法: 内部ポインターおよびマネージド配列を宣言および使用する (C++/CLI)

次の C +/cli CLI のサンプルを宣言して、配列への内部ポインターを使用する方法を示しています。

> [!IMPORTANT]
> この言語機能がサポートされている、`/clr`コンパイラ オプションがなく、`/ZW`コンパイラ オプション。

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// interior_ptr_arrays.cpp
// compile with: /clr
#define SIZE 10

int main() {
   // declare the array
   array<int>^ arr = gcnew array<int>(SIZE);

   // initialize the array
   for (int i = 0 ; i < SIZE ; i++)
      arr[i] = i + 1;

   // create an interior pointer into the array
   interior_ptr<int> ipi = &arr[0];

   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);

   ipi++;
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);
}
```

```Output
1st element in arr holds: 1
ipi points to memory address whose value is: 1
after incrementing ipi, it points to memory address whose value is: 2
```

## <a name="see-also"></a>関連項目

[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)