---
title: コンパイラの警告 (レベル 1) C4747 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d3eb5b83fedc7455cbf1b97119296a6eb6a1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118480"
---
# <a name="compiler-warning-level-1-c4747"></a>コンパイラの警告 (レベル 1) C4747

呼び出すマネージ 'entrypoint': マネージ コードは DLL エントリ ポイントおよび DLL エントリ ポイントから到達した呼び出しを含むローダー ロック下で実行できません

コンパイラは、MSIL にコンパイル (可能性の高い) DLL エントリ ポイントを検出します。  エントリ ポイントが MSIL にコンパイルされた DLL を読み込むと潜在的な問題のため MSIL に DLL エントリ ポイント関数のコンパイルを強くお勧めしています。

詳細については、次を参照してください。[混在アセンブリの初期化](../../dotnet/initialization-of-mixed-assemblies.md)と[リンカー ツール エラー LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)します。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 使用して、モジュールをコンパイルしないで **/clr**します。

1. 使用して、エントリ ポイント関数をマーク`#pragma unmanaged`します。

## <a name="example"></a>例

次の例では、C4747 が生成されます。

```
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```