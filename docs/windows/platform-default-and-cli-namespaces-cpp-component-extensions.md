---
title: プラットフォーム、既定では、および cli 名前空間 (C +/cli および C++/cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a70fb5317f42e98ccddb21fe66e328e1cc6f7643
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328026"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>プラットフォーム、既定では、および cli 名前空間 (C +/cli および C++/cli CX)

言語要素の名前は名前空間によって修飾されるため、それ以外は同じである名前と、ソース コードの別の部分で競合することはありません。 たとえば、名前の競合は弱くコンパイラを妨げる可能性[状況依存のキーワード](../windows/context-sensitive-keywords-cpp-component-extensions.md)します。 名前空間はコンパイラによって使用されますが、コンパイルされたアセンブリでは保持されません。

## <a name="all-runtimes"></a>すべてのランタイム

Visual Studio では、プロジェクトを作成するときに、プロジェクトの既定の名前空間を提供します。 C + で、名前空間を手動で変更できます/cli CX .winmd ファイルの名前は、ルート名前空間の名前と一致する必要があります。

## <a name="windows-runtime"></a>Windows ランタイム

詳細については、次を参照してください。[名前空間と型の可視性 (C + + CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx)します。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="syntax"></a>構文

```cpp
using namespace cli;
```

### <a name="remarks"></a>Remarks

C++/cli CLI は、サポート、 **cli**名前空間。 コンパイルするときに`/clr`、**を使用して**「構文」セクション内ステートメント暗黙的に指定します。

次の言語機能で、 **cli**名前空間。

- [配列](../windows/arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次のコード例に示しますを内のシンボルを使用することは、 **cli**コード内のユーザー定義シンボルとして名前空間。  ただし、これを完了したら、必要があります明示的または暗黙的にへの参照を修飾するために、 **cli**同じ名前の言語要素です。

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>関連項目

[Component Extensions for .NET と UWP](../windows/component-extensions-for-runtime-platforms.md)