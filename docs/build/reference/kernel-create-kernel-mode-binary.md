---
title: -カーネル (作成カーネル モード バイナリ) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02c5d8cff2d57a9dc8bfac31c4806a976d58859d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716795"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (カーネル モード バイナリの作成)

Windows カーネルで実行できるバイナリを作成します。

## <a name="syntax"></a>構文

```
/kernel[-]
```

## <a name="arguments"></a>引数

**/kernel**<br/>
現在のプロジェクトでコードがコンパイルされ、カーネル モードで実行されるコードに固有の C++ 言語の規則のセットを使用してリンクします。

**/kernel-**<br/>
現在のプロジェクトでコードがコンパイルされ、カーネル モードで実行されるコードに固有の C++ 言語の規則を使用せずにリンクさせます。

## <a name="remarks"></a>Remarks

`#pragma` には、このオプションを制御するための相当するものはありません。

指定する、 **/kernel**オプションは、コンパイラとリンカーの言語機能はカーネル モードで許容されるかを判別し、ランタイムが不安定になるに一意を回避するための十分な表現力があることを確認するにはカーネル モード C++ です。 これは、カーネル モードで中断を伴う C++ 言語の機能の使用を禁止することで、警告は、潜在的な混乱が無効にすることはできませんが、C++ 言語の機能を提供することで実現されます。

**/Kernel**オプションは、ビルドのコンパイラとリンカーの両方のフェーズに適用され、プロジェクト レベルで設定されています。 渡す、 **/kernel**を結果のバイナリにリンクしたら、読み込むこと、Windows カーネルにコンパイラに示すスイッチです。 コンパイラが、さまざまな C++ 言語の機能をカーネルと互換性があるサブセットに絞り込まれます。

次の表に、コンパイラの動作の変更時に **/kernel**を指定します。

|動作の種類|**/kernel**動作|
|-------------------|---------------------------|
|C++ 例外処理|無効になります。 すべてのインスタンス、`throw`と`try`キーワードはコンパイラ エラーを生成 (例外の指定を除く`throw()`)。 いいえ **/EH**オプションと互換性のある **/kernel**を除く **/EH-**。|
|RTTI|無効になります。 すべてのインスタンス、`dynamic_cast`と`typeid`キーワードが、コンパイラ エラーを出力しない限り、`dynamic_cast`静的に使用されます。|
|`new` および `delete`|明示的に定義する必要があります、`new()`または`delete()`演算子は、コンパイラも、ランタイムでもないに default 定義を指定します。|

呼び出し規則、カスタム、 [/GS](../../build/reference/gs-buffer-security-check.md)を使用する場合に、許可されるビルド オプション、およびすべての最適化、 **/kernel**オプション。 インライン展開はほとんど受けません **/kernel**、コンパイラによって受け入れと同じセマンティクスを持つ。 確認する場合、`__forceinline`インライン展開の修飾子を受け入れ、必ずその警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)特定がわかるようにが有効になって`__forceinline`関数はインラインではありません。

コンパイラが渡された場合、 **/kernel**スイッチが事前に定義するプリプロセッサ マクロは、という`_KERNEL_MODE`と値を保持**1**します。 条件付きで実行環境がユーザー モードまたはカーネル モードがかどうかに基づいてコードをコンパイルするのにには、これを使用できます。 たとえば、次のコードでは、カーネル モード実行のコンパイル時にクラスが非ページング メモリ セグメントであることを指定します。

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

いくつか次のターゲット アーキテクチャの組み合わせと **/arch**オプションを使用するときにエラーが発生 **/kernel**:

- **/arch: {SSE&#124;SSE2&#124;AVX}** は x86 上でサポートされていません。 のみ **/arch:IA32**ではサポートされて **/kernel** x86。

- **/arch:AVX**はサポートされていません **/kernel** x64。

使用した構築 **/kernel**も渡す **/kernel**リンカーにします。 彼女は、リンカーの動作に与える影響を示します。

- インクリメンタル リンクが無効です。 追加する場合 **/incremental**リンカーは、コマンドラインにこの致命的なエラーを出力します。

   **リンク: 致命的なエラー LNK1295: '/増分' と互換性がない '/カーネル ' の指定。リンク '/incremental' なし**

- 各オブジェクト ファイル (または静的ライブラリから、含まれるアーカイブ メンバー) を確認するかどうか、でしたコンパイルされているを使用して、リンカーが検査、 **/kernel**オプションでした。 すべてのインスタンスは、この条件を満たす、リンカーが、まだ正常にリンクしますが、次の表に示すように警告を発行する可能性があります。

   ||**/kernel** obj|**/kernel-** obj、MASM obj、または cvtresed|混在 **/kernel**と **/kernel-** obj|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**リンク/kernel**|はい|はい|警告 LNK4257 ○ します。|
   |**リンク**|はい|[はい]|はい|

   **LNK4257/KERNEL; でコンパイルされないオブジェクトのリンクイメージは動作しない可能性があります。**

**/Kernel**オプションと **/driver**オプションは独立して動作し、他のどちらに影響します。

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Visual Studio で/kernel コンパイラ オプションを設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、「[プロジェクト プロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加`/kernel`または`/kernel-`します。

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)