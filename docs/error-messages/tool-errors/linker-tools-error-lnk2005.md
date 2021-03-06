---
title: リンカ ツール エラー LNK2005 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3dbb1d63e7d7c6f5e036fc0cde967277c91a40
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890128"
---
# <a name="linker-tools-error-lnk2005"></a>リンカ ツール エラー LNK2005

> *シンボル*オブジェクトで既に定義されています。

シンボル*シンボル*複数回定義されました。

このエラーは致命的なエラー続けて[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)します。

### <a name="possible-causes-and-solutions"></a>考えられる原因と解決策

通常、このエラーが破損した、*単一定義規則*、全体の実行可能ファイルの間で、使用するテンプレート、関数、型、または、指定されたオブジェクト ファイル内のオブジェクトの 1 つだけの定義で、1 つだけ定義できます外部から参照できるオブジェクトまたは関数。

このエラーの一般的な原因を示します。

- このエラーは、ヘッダー ファイルの変数を定義するときに発生することができます。 たとえば、プロジェクトでは、複数のソース ファイルでこのヘッダー ファイルをインクルードする場合は、エラーが発生します。

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   次の解決策が考えられます。

   - 変数を宣言`extern`ヘッダー ファイル:`extern int global_int;`指定してから、必要に応じて、1 つのソース ファイル内で初期化:`int global_int = 17;`します。 この変数は、グローバルなようになりましたことを宣言することで任意のソース ファイルで使用できる`extern`、たとえば、ヘッダー ファイルを含めることで。 変数、グローバルである必要がありますが、このソリューションをお勧めしますが、優れたソフトウェア エンジニア リング プラクティスには、グローバル変数が最小限に抑えられます。

   - 変数を宣言して[静的](../../cpp/storage-classes-cpp.md#static):`static int static_int = 17;`します。 これを現在のオブジェクト ファイルに定義のスコープを制限し、変数の独自のコピーが複数のオブジェクト ファイルできます。 ヘッダー ファイルで静的変数を定義するグローバル変数との混同する可能性のためお勧めしません。 優先すると、それらを使用するソース ファイル静的変数の定義に移動します。

   - 変数を宣言して[selectany](../../cpp/selectany.md):`__declspec(selectany) int global_int = 17;`します。 すべての外部参照で使用するための 1 つの定義を選択して、残りは破棄をリンカーに指示します。 このソリューションはインポート ライブラリを結合するときに便利です。 それ以外の場合、お勧めしませんリンカー エラーを回避する手段として。

- このエラーは、ヘッダー ファイルがない関数を定義する場合に発生する可能性が`inline`します。 1 つ以上のソース ファイルでこのヘッダー ファイルを含めると、実行可能ファイルで、関数の複数の定義を取得します。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   次の解決策が考えられます。

   - 追加、`inline`関数にキーワード。

        ```h
        // LNK2005_func_inline.h
        inline int sample_function(int k) { return 42 * (k % 167); }
        ```

   - ヘッダー ファイルから、関数本体を削除して、宣言のみのままにし、1 つのソース ファイル内の関数を実装します。

        ```h
        // LNK2005_func_decl.h
        int sample_function(int);
        ```

        ```cpp
        // LNK2005_func_impl.cpp
        int sample_function(int k) { return 42 * (k % 167); }
        ```

- このエラーは、ヘッダー ファイルで、クラス宣言の外側のメンバー関数を定義する場合にも発生します。

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   この問題を解決するには、メンバー関数の定義、クラス内を移動します。 クラス宣言内で定義されているメンバー関数は、暗黙的にインライン化されます。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- このエラーは、CRT または標準ライブラリの 1 つ以上のバージョンをリンクする場合に発生することができます。 たとえば、両方の製品版とデバッグ CRT ライブラリでは、またはライブラリの静的および動的な両方のバージョンまたは標準ライブラリの 2 つの異なるバージョンを実行可能ファイルにリンクしようとした場合このエラー可能性があります報告される何度もします。 この問題を解決するには、link コマンドから各ライブラリのすべてが 1 つのコピーを削除します。 製品版を混在させるし、ライブラリ、または別のバージョンの同じ実行可能ファイル、ライブラリのデバッグはお勧めできません。

   使用し、使用するライブラリを指定、コマンドラインで、既定値以外のライブラリを使用するようにリンカーに指示する、 [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)の既定のライブラリを無効にするオプション。 IDE を開き、使用するライブラリを指定するプロジェクトへの参照を追加、**プロパティ ページ**で、プロジェクトのダイアログ ボックス、**リンカー**、**入力**プロパティいずれかの設定 ページで、**既定ライブラリをすべて無視**、または**特定の既定のライブラリの無視**プロパティの既定のライブラリを無効にします。

- 使用する場合、静的および動的なライブラリの使用を混在している場合、このエラーが発生することができます、 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)オプション。 たとえば、実行可能ファイル、静的な CRT にリンクするで使用するための DLL にビルドする場合に、このエラーが発生することができます。 この問題を解決するには、ビルド、実行可能ファイルで使用するすべてのライブラリと実行可能ファイル全体のスタティック ライブラリのみまたは動的ライブラリのみを使用します。

- シンボルがパッケージ化された関数の場合、このエラーが発生することができます (でコンパイルして作成された[/Gy](../../build/reference/gy-enable-function-level-linking.md)) と 1 つ以上のファイルに含まれていたが、コンパイルの間で変更されました。 この問題を解決するには、パッケージ化された関数を含むすべてのファイルを再コンパイルします。

- シンボルがさまざまなライブラリで 2 つのメンバー オブジェクトに異なる方法で定義されているし、両方のメンバー オブジェクトが使用される場合、このエラーが発生することができます。 ライブラリが静的にリンクされている場合は、この問題を解決する方法の 1 つは、1 つだけのライブラリからメンバー オブジェクトを使用して、リンカー コマンドラインに最初にそのライブラリを含めるは。 両方のシンボルを使用するには、それらを区別する方法を作成する必要があります。 たとえば、ソースからのライブラリをビルドする場合は、一意の名前空間内の各ライブラリをラップできます。 または、一意の名前を使用して、元のライブラリのいずれかへの参照をラップし、元のライブラリに新しいライブラリをリンクし、実行可能ファイルを元のライブラリではなく、新しいライブラリにリンクする新しいラッパー ライブラリを作成することができます。

- 場合に、このエラーが発生することができます、`extern const`変数が 2 回、定義されているし、それぞれの定義で別の値を持ちます。 この問題を解決するには、一度だけ定数を定義または名前空間を使用または`enum class`定数を区別するために定義します。

- このエラーは、Guid (oledb.lib や adsiid.lib など) を定義する他の .lib ファイルと組み合わせて uuid.lib を使用する場合に発生することができます。 例えば:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   この問題を解決するには追加[/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md)その uuid.lib が最初に参照されるライブラリをリンカー コマンドラインのオプションを確認します。
