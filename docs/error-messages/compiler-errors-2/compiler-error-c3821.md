---
title: コンパイラ エラー C3821 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3821
dev_langs:
- C++
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e1f9a0bbb8eaae6b316b3d00e4201b2b64222ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023034"
---
# <a name="compiler-error-c3821"></a>コンパイラ エラー C3821

'function': マネージ型または関数は、アンマネージ関数で使用できません

インライン アセンブリでの関数または[setjmp](../../c-runtime-library/reference/setjmp.md)値の型またはマネージ クラスを含めることはできません。 このエラーを解決するには、インライン アセンブリを削除し、`setjmp`またはマネージ オブジェクトを削除します。

C3821 は、自動ストレージ vararg 関数で使用しようとする場合にも発生します。  詳細については、次を参照してください[可変個引数リスト (...)。(C +/CLI CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)と[参照型の C++ スタック セマンティクス](../../dotnet/cpp-stack-semantics-for-reference-types.md)します。

## <a name="example"></a>例

次の例では、C3821 が生成されます。

```
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>例

次の例では、C3821 が生成されます。

```
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
