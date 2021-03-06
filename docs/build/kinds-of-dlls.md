---
title: Dll の種類 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca646c39bbe99ba4ed4059f350d9478b669d408
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710178"
---
# <a name="kinds-of-dlls"></a>DLL の種類

ここで説明する情報は、ビルドする DLL の種類を決定するときの参考になります。

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> 使用可能な Dll の種類

Visual C++ を使うと、C または C++ で MFC ライブラリを使わない Win32 DLL をビルドできます。 Win32 アプリケーション ウィザードでは、非 MFC DLL プロジェクトを作成できます。

MFC DLL ウィザードでは、スタティック リンク ライブラリでも、多くの DLL でも、MFC ライブラリ自体を利用できます。 MFC を利用する DLL は、Visual C++ では次の 3 とおりの方法で開発できます。

- MFC とリンク ビルド レギュラー MFC DLL を静的に

- MFC とリンク ビルド レギュラー MFC DLL を動的に

- 常に MFC と動的にリンクする MFC 拡張 DLLをビルド

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [非 MFC DLL: 概要](../build/non-mfc-dlls-overview.md)

- [MFC と静的にリンクされるレギュラー MFC の Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [MFC と動的にリンクされるレギュラー MFC の Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 拡張 DLL: 概要](../build/extension-dlls-overview.md)

- [使用する DLL の決定](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> 使用する DLL の決定

DLL で MFC を使用しない場合、Visual C++ を使って非 MFC Win32 DLL をビルドします。 リンクの形態が静的か動的かにかかわらず、MFC とリンクする DLL は、ディスク領域とメモリをかなり使用します。 実際に MFC を使わない DLL は、MFC とリンクしないでください。

DLL が MFC を使用する MFC または非 MFC アプリケーションで使用される場合は、MFC と動的にリンクされるレギュラー MFC DLL または MFC を静的にリンクされるレギュラー MFC DLL のいずれかをビルドする必要があります。 ほとんどの場合、おそらく、DLL のファイル サイズが大幅に小さくして、MFC の共有バージョンを使用するとメモリを大幅に節約がかなり大きくなるため、MFC と動的にリンクされるレギュラー MFC DLL を使用するします。 MFC と静的にリンクする場合は、MFC ライブラリ コードの専用コピーを読み込むために、DLL のファイル サイズは大きくなり、余分なメモリを使用する可能性があります。

動的リンクの場合には MFC 自体をリンクする必要がないため、ビルド処理は静的にリンクされる DLL よりも動的にリンクされる DLL の方が高速です。 この傾向は、リンカーがデバッグ情報を圧縮する必要があるデバッグ ビルドについて特に顕著になります。 デバッグ情報を既に含む DLL とリンクすることによって、DLL 内に圧縮されるデバッグ情報が少なくなります。

MFC との動的リンクの欠点として、MFCx0.dll と Msvcrxx.dll (または同様のファイル) という共有 DLL を一緒に配布する必要性が生じる点を挙げることができます。 MFC DLL の再配布は自由ですが、セットアップ プログラムで DLL をインストールする必要があります。 さらに、プログラムと MFC DLL 自体の双方が使用する C ランタイム ライブラリを含む Msvcrxx.dll も同梱する必要があります。

DLL は MFC の実行可能ファイルでのみ使用される、いずれかをレギュラー MFC DLL または MFC 拡張 DLL をビルドする必要があります。 既存の MFC クラスから派生した再利用可能なクラスを DLL に実装、またはアプリケーションと DLL の間 MFC の派生オブジェクトを渡す必要がある、MFC 拡張 DLL をビルドする必要があります。

MFC と動的にリンクされる DLL では、DLL と共に MFC DLL を再配布することもあります。 このアーキテクチャでは、使用ディスク領域が抑制され、メモリの使用も最小化されるため、複数の実行可能ファイル間でクラス ライブラリを共有する場合に特に便利です。

バージョン 4.0 までは、Visual C++ は MFC を使う DLL として、USRDLL と AFXDLL の 2 種類しかサポートしていませんでした。 MFC と静的にリンクされるレギュラー MFC の Dll には、USRDLL と同じ特性があります。 MFC 拡張 DLL は、これまでの AFXDLL と同じ性質を持っています。

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [非 MFC DLL: 概要](../build/non-mfc-dlls-overview.md)

- [MFC と静的にリンクされるレギュラー MFC の Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [MFC と動的にリンクされるレギュラー MFC の Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 拡張 DLL: 概要](../build/extension-dlls-overview.md)

## <a name="see-also"></a>関連項目

[Visual C++ の DLL](../build/dlls-in-visual-cpp.md)