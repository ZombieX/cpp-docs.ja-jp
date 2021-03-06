---
title: 概要の x64 呼び出し規則 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e70f4017cb31fcc76b1cf3ef2a77d3a28e31bd28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707994"
---
# <a name="overview-of-x64-calling-conventions"></a>x64 呼び出し規則の概要

X86 および x64 の 2 つの重要な違いは、64 ビットのアドレス指定機能および一般的な用途のレジスタを 16 個の 64 ビットのフラットなセット。 展開されたレジスタ セットを指定するには、x64 を使用して、 [_ _fastcall](../cpp/fastcall.md)呼び出し規約および RISC ベースの例外処理モデル。 `__fastcall`規則では、最初の 4 つの引数とスタック フレームのレジスタを使用して、追加の引数を渡します。

次のコンパイラ オプションでは、x64 用のアプリケーションを最適化するのに役立ちます。

- [/favor (アーキテクチャ固有の最適化)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="calling-convention"></a>呼び出し規則

既定のアプリケーション バイナリ インターフェイス (ABI) によって、4 つのレジスタ高速呼び出しの呼び出し規約を使用して x64 です。 これらのレジスタを保存する呼び出し先のシャドウ ストアとしてコール スタックに領域が割り当てられます。 関数呼び出しに引数とそれらの引数に使用されるレジスタの間は、厳密な一対一で対応します。 8 バイトに収まらないまたは 1、2、4、または 8 バイトではない任意の引数は、参照渡しで渡す必要があります。 1 つの引数を複数のレジスタに分散しようとすることはありません。 X87 レジスタ スタックは使用されません。 呼び出し先で使用できますが、考慮する必要が揮発性関数呼び出しで。 すべての浮動小数点操作が完了したら個の XMM レジスタを 16 を使用します。 整数の引数が RCX、RDX、R8、および R9 レジスタに渡されます。 浮動小数点引数は XMM0L、XMM1L、XMM2L、および XMM3L で渡されます。 16 バイトの引数は、参照によって渡されます。 パラメーターの引き渡しがで詳しく説明されている[パラメーターの引き渡し](../build/parameter-passing.md)します。 これらのレジスタだけでなく RAX、R10、R11、XMM4、および XMM5 と見なされます揮発性。 その他のすべてのレジスタは、非揮発性です。 レジスタの使用量の詳細に記載されている[Usage の登録](../build/register-usage.md)と[呼び出し元/呼び出し先保存登録](../build/caller-callee-saved-registers.md)します。

呼び出し元は、呼び出し先へのパラメーター領域を割り当てる必要があり、呼び出し先はそれほど多くのパラメーターを受け取るしない場合でも常に、4 つの登録パラメーターを格納するための十分な領域を割り当てる必要があります。 これには、プロトタイプ宣言されていない C 言語の関数、および vararg C と C++ の関数のサポートが簡略化します。 Vararg またはプロトタイプ宣言されていない関数では、任意の浮動小数点値をする必要があります、対応する汎用レジスタ内で重複します。 最初の 4 つを超えるすべてのパラメーターは、呼び出しの前に、最初の 4 つのシャドウ ストア上のスタックに格納する必要があります。 Vararg 関数の詳細が記載されて[Varargs](../build/varargs.md)します。 プロトタイプ宣言されていない関数についての詳細については[プロトタイプ宣言されていない関数](../build/unprototyped-functions.md)します。

## <a name="alignment"></a>アラインメント

ほとんどの構造体は、自然なアラインメントに揃えて配置されます。 プライマリの例外は、スタック ポインターと`malloc`または`alloca`メモリで、パフォーマンスを支援するために、16 バイトに揃えられます。 16 バイトを超える配置を手動で行う必要がありますが、これはほとんどのコードの動作 XMM 操作の一般的な配置のサイズを 16 バイトには、します。 構造体レイアウトやアラインメントの詳細については、次を参照してください。[型とストレージ](../build/types-and-storage.md)します。 スタックのレイアウトについては、次を参照してください。 [Stack の Usage](../build/stack-usage.md)します。

## <a name="unwindability"></a>Unwindability

リーフ関数は、任意の非 volatile レジスタが変更されない関数です。 非リーフ関数は、関数を呼び出すか、ローカル変数の追加のスタック領域の割り当てによって、非揮発性 RSP をたとえば、変更できます。 例外を処理するときに非 volatile レジスタを回復するには、非リーフ関数を正しく任意命令に関数をアンワインドする方法を説明する静的データで注釈する必要があります。 このデータとして格納されます*pdata*、またはプロシージャのデータは、順番を指す*xdata*、例外データを処理します。 Xdata アンワインドの情報を格納し、追加 pdata または例外のハンドラー関数を指すことができます。 プロローグとエピローグは、正しく xdata で説明されている可能性があるように高度に制限されます。 スタック ポインターは、16 バイトのプロローグまたはエピローグの一部を除くリーフ関数の中でないコードを任意のリージョン内に配置する必要があります。 リーフ関数は、pdata および xdata は必要ありませんので、戻り値をシミュレートするだけでさかのぼることができます。 詳細については、関数プロローグとエピローグの適切な構造は、次を参照してください。[プロローグとエピローグ](../build/prolog-and-epilog.md)します。 例外処理、および例外処理アンワインディング pdata と xdata の詳細については、次を参照してください。[例外処理 (x64)](../build/exception-handling-x64.md)します。

## <a name="see-also"></a>関連項目

[x64 ソフトウェア規約](../build/x64-software-conventions.md)