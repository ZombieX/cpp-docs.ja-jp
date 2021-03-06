---
title: '例外処理: MFC 例外マクロの変換 |Microsoft Docs'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 692814a189a4f64cbd1e11e4c8cc4741e2d2dc99
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212627"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>例外処理 : 古いコードの変換

これは、高度なトピックです。

この記事は、Microsoft Foundation Class のマクロで記述された既存のコードに変換する方法を説明します:**お試しください**、**キャッチ**、**スロー**など -C++ 例外処理を使用するにはキーワード**お試しください**、**キャッチ**、および**スロー**します。 ここでは、次の内容について説明します。

- [変換の利点があります。](#_core_advantages_of_converting)

- [C++ 例外を使用する例外処理マクロを使用したコードを変換します。](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> 変換の利点

おそらく必要はありません、既存のコードを変換するが、mfc バージョン 3.0 マクロ実装と以前のバージョンの実装間の相違があります。 これらの相違点とそれ以降のコードの動作変更については[例外: Version 3.0 での例外処理マクロを変更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)します。

変換の主なメリットは次のとおりです。

- C++ 例外処理のキーワードを使用するコードを若干小さいをコンパイルします。EXE またはします。DLL です。

- C++ 例外処理キーワードより汎用性の高い: コピーできる任意のデータ型の例外を処理できるように (**int**、 **float**、 **char**など) であるのに対し、マクロのみクラスの例外を処理する`CException`とその派生クラス。

マクロとキーワードの主な違いは、例外がスコープから外れたときに、「自動的に」マクロを使用して、コードは、キャッチされた例外を削除します。 です。 キーワードを使用して、コードはしていないため、キャッチされた例外を明示的に削除する必要があります。 詳細については、この記事を参照してください。[例外。 例外のキャッチと削除](../mfc/exceptions-catching-and-deleting-exceptions.md)します。

別の相違点は、構文です。 マクロとキーワードの構文は、次の 3 つの点で異なります。

1. マクロの引数と例外の宣言

   A**キャッチ**マクロ呼び出しは、次の構文。

   **キャッチ (** *exception_class*、*ことは* **)**

   クラス名とオブジェクト ポインター名のコンマに注意してください。

   例外宣言、**キャッチ**キーワードは、この構文を使用します。

   **キャッチ (** *exception_type* *exception_name* **)**

   このステートメントを catch の例外の種類を示しますブロックで処理します。

2. Catch ブロックの区切り。

   マクロで、**キャッチ**マクロ (とその引数) は、最初の catch ブロックを開始、 **AND_CATCH**マクロは、後続の catch ブロックを開始し、 **END_CATCH**マクロcatch ブロックのシーケンスを終了します。

   キーワードで、**キャッチ**キーワード (例外宣言) では、各 catch ブロックを開始します。 相当するはありません、 **END_CATCH**マクロは、catch ブロックの右中かっこで終了します。

3. スロー式:

   マクロを使用して、 **THROW_LAST**再び現在の例外をスローします。 **スロー**キーワードを引数なしで同じ効果があります。

##  <a name="_core_doing_the_conversion"></a> 変換を行う

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>C++ 例外処理キーワードを使用するマクロを使用してコードを変換するには

1. MFC のマクロのすべてのアイテムを見つけて**お試しください**、**キャッチ**、 **AND_CATCH**、 **END_CATCH**、**スロー**、**THROW_LAST**します。

2. 置換、または以下のマクロのすべての出現箇所を削除します。

   **お試しください**(コードに置き換えます**お試しください**)

   **キャッチ**(コードに置き換えます**キャッチ**)

   **AND_CATCH** (コードに置き換えます**キャッチ**)

   **END_CATCH** (削除)

   **スロー** (コードに置き換えます**スロー**)

   **THROW_LAST** (コードに置き換えます**スロー**)

3. 有効な例外宣言を形成するために、マクロの引数を変更します。

   たとえば、変更します。

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   から

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 必要に応じて、例外オブジェクトを削除するために、catch ブロックで、コードを変更します。 詳細については、この記事を参照してください。[例外。 例外のキャッチと削除](../mfc/exceptions-catching-and-deleting-exceptions.md)します。

MFC 例外マクロを使用して例外処理コードの例を次に示します。 次の例のコードは、マクロ、例外を使用しているため`e`自動的に削除されます。

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

次の例のコードは、例外を明示的に削除する必要がありますので、C++ の例外のキーワードを使用します。

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

詳細については、次を参照してください。[例外: を使用して MFC マクロと C++ 例外](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)します。

## <a name="see-also"></a>関連項目

[例外処理](../mfc/exception-handling-in-mfc.md)<br/>
