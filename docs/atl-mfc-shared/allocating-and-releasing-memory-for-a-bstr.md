---
title: BSTR のメモリの解放の割り当てと |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- bstr
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 565032ca7ddf64e93716b1c06524bd09a1a46079
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389396"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>BSTR 用のメモリの割り当てと解放

作成するときに`BSTR`s と COM オブジェクトの間で渡さないで、メモリ リークを回避するために使用するメモリを扱うことでように注意する必要があります。 ときに、`BSTR`インターフェイス内でまだ、終了するときにメモリを解放する必要があります。 ただし、ときに、`BSTR`インターフェイスからパスは、受信側のオブジェクトは、メモリ管理を担当します。

割り当てとメモリを解放するための規則に割り当てられた一般に、`BSTR`は次のようにします。

- 予期される関数を呼び出すと、`BSTR`引数用のメモリを割り当てる必要があります、`BSTR`呼び出しの前に、後でリリースします。 例えば:

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- 返す関数を呼び出すと、 `BSTR`、自分で文字列を解放する必要があります。 例えば:

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- 返す関数を実装する場合、`BSTR`文字列を割り当てますが、解放しないでください。 受信関数は、メモリを解放します。 例えば:

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>関連項目

[文字列 (ATL と MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysfreestring)

