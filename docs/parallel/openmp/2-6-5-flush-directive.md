---
title: 2.6.5 flush ディレクティブ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d67453b636d50fcb78092318ebb76f5192817548
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442735"
---
# <a name="265-flush-directive"></a>2.6.5 flush ディレクティブ

**フラッシュ**ディレクティブで明示的または黙示に関わらず、かどうかは実装が現在チームのすべてのスレッドは、特定のオブジェクト (指定された) の下での一貫性のあるビューでいることを確認に必要な場合は、「スレッド間」シーケンス ポイントを指定しますメモリ。 これは、前のこれらのオブジェクトを参照する式の評価が完了し、以降の評価はまだ開始していないことを意味します。 たとえば、コンパイラは、メモリにレジスタからのオブジェクトの値を復元する必要があり、ハードウェアは、メモリへの書き込みバッファーをフラッシュし、メモリからオブジェクトの値を再読み込みする必要があります。

構文、**フラッシュ**ディレクティブを次に示します。

```
#pragma omp flush [(variable-list)]  new-line
```

同期が必要なオブジェクトすべて指定するには、変数で、省略可能なこれらの変数を指定することができる場合*変数一覧*します。 ポインターがある場合、*変数一覧*、ポインター自体がフラッシュされる、オブジェクトではなく、ポインターが参照します。

A**フラッシュ**せずディレクティブ、*変数一覧*自動ストレージ存続期間とアクセスできないオブジェクトを除くすべての共有オブジェクトを同期します。 (よりも多くのオーバーヘッドがある可能性があります、**フラッシュ**で、*変数一覧*)。A**フラッシュ**せずディレクティブ、*変数一覧*が暗黙的に次のディレクティブの指定します。

- `barrier`

- エントリにしてから終了に**重大**

- エントリとからの終了 `ordered`

- エントリにしてから終了に**並列**

- At 終了**の**

- At 終了**セクション**

- At 終了**単一**

- エントリにしてから終了に**の並列**

- エントリにしてから終了に**並列セクション**

場合に、ディレクティブは示されません、`nowait`句が存在します。 注意するべきことを**フラッシュ**ディレクティブは、次のいずれかの暗黙的に指定できません。

- 入る**の**

- エントリをまたはからの終了時に**マスター**

- 入る**セクション**

- 入る**単一**

Volatile で修飾された型のオブジェクトの値にアクセスするための参照があった場合と同様に、**フラッシュ**ディレクティブの前のシーケンス ポイントにそのオブジェクトを指定します。 Volatile で修飾された型のオブジェクトの値を変更するための参照があった場合と同様に、**フラッシュ**後続シーケンス ポイントにそのオブジェクトを指定するディレクティブ。

ため、**フラッシュ**ディレクティブには、その構文の一部として、C 言語のステートメントはありません。、、、プログラム内で配置する場合に制限があります。 参照してください[付録 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式な文法についてはします。 次の例では、これらの制限事項を示します。

```
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

制限は、**フラッシュ**ディレクティブは、次のとおり。

- 指定される変数を**フラッシュ**ディレクティブが参照型に必要ありません。