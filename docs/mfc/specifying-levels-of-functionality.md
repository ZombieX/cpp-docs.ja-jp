---
title: 機能レベルを指定する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 765a5293f233cb6df0654416ea2a5463df1095a8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054424"
---
# <a name="specifying-levels-of-functionality"></a>継承機能のレベルの指定

この記事は、次の機能レベルを追加する方法を説明します、 [CObject](../mfc/reference/cobject-class.md)-クラスを派生します。

- [ランタイム クラス情報](#_core_to_add_run.2d.time_class_information)

- [動的な作成サポート](#_core_to_add_dynamic_creation_support)

- [シリアル化のサポート](#_core_to_add_serialization_support)

一般的な説明について`CObject`機能、記事をご覧ください[CObject からクラスを派生する](../mfc/deriving-a-class-from-cobject.md)します。

- [ランタイム クラス情報](#_core_to_add_run.2d.time_class_information)
#### <a name="_core_to_add_run.2d.time_class_information"></a> ランタイム クラス情報を追加するには

1. クラスを派生`CObject`」の説明に従って、 [CObject からクラスを派生する](../mfc/deriving-a-class-from-cobject.md)記事。

1. 次に示すように、クラス宣言 DECLARE_DYNAMIC マクロを使用します。

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. IMPLEMENT_DYNAMIC マクロを使用して、実装ファイル (します。CPP) のクラス。 このマクロは引数として受け取り、クラスと、その基底クラスの名前には、次のように。

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
>  常に新規クラスを実装ファイルに配置 (します。CPP) クラス。 IMPLEMENT_DYNAMIC マクロは、コンパイル時に 1 回だけ評価される必要があり、そのため、インターフェイス、ファイルでは使用できません (します。H) は 1 つ以上のファイルに含める可能性のある可能性があります。

#### <a name="_core_to_add_dynamic_creation_support"></a> 動的な作成サポートを追加するには

1. クラスを派生`CObject`します。

1. クラス宣言で DECLARE_DYNCREATE マクロを使用します。

1. (既定のコンス トラクター) を引数なしのコンス トラクターを定義します。

1. クラスの実装ファイルには、IMPLEMENT_DYNCREATE マクロを使用します。

#### <a name="_core_to_add_serialization_support"></a> シリアル化のサポートを追加するには

1. クラスを派生`CObject`します。

1. 上書き、`Serialize`メンバー関数。

    > [!NOTE]
    >  呼び出す場合`Serialize`直接、つまり、たくないポリモーフィックなポインターを使用してオブジェクトをシリアル化、手順 3. ~ 5. を省略します。

1. クラス宣言で DECLARE_SERIAL マクロを使用します。

1. (既定のコンス トラクター) を引数なしのコンス トラクターを定義します。

1. IMPLEMENT_SERIAL マクロを使用して、クラス ファイルに実装します。

> [!NOTE]
>  「ポリモーフィックなポインター」は、クラスのオブジェクトを指します (付けます A) または、(たとえば、B) から派生したクラスのオブジェクト。 ポリモーフィックなポインターを通じて、シリアル化するには、フレームワークがいくつかの基本クラス (A) から派生したクラスのオブジェクトがある可能性があるために、(B) をシリアル化するオブジェクトのランタイム クラスを判別する必要があります。

クラスを派生させる場合は、シリアル化を有効にする方法の詳細については`CObject`、記事を参照して[MFC のファイル](../mfc/files-in-mfc.md)と[シリアル化](../mfc/serialization-in-mfc.md)します。

## <a name="see-also"></a>関連項目

[CObject からのクラスの派生](../mfc/deriving-a-class-from-cobject.md)
