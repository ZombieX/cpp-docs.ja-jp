---
title: 配置の概念 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea2039cd9fa1c5071da143f557406d028f464d7e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676709"
---
# <a name="deployment-concepts"></a>配置の概念

このセクションでは、C++ アプリケーションの配置に関する主な考慮事項について説明します。

## <a name="windows-installer-deployment-in-c"></a>C++ での Windows インストーラーの配置

Visual C++ では、通常、配置用の従来の Windows インストーラー セットアップを使用します。 Windows インストーラーの配置を準備するには、setup.exe ファイルにアプリケーションをパッケージ化し、インストーラー パッケージ (.msi) と共に、そのファイルを配布します。 その後、ユーザーは setup.exe を実行して、アプリケーションをインストールします。

アプリケーションをパッケージ化するには、セットアップ プロジェクトをソリューションに追加します。これにより、ユーザーに配布するセットアップおよびインストーラー パッケージ ファイルがビルド時に作成されます。 詳細については、「[配置方法の選択](../ide/choosing-a-deployment-method.md)」を参照してください。

## <a name="library-dependencies"></a>ライブラリの依存ファイル

Visual C++ ライブラリで提供される機能を使用して C/C++ アプリケーションをビルドすると、そのアプリケーションは実行時にそれらのライブラリの存在に依存するようになります。 アプリケーションを実行するには、必要な Visual C++ ライブラリに静的または動的にリンクする必要があります。 アプリケーションが動的に Visual C++ ライブラリにリンクしている場合、アプリケーションの実行時には、そのライブラリが存在し、読み込むことができる必要があります。 それに対して、アプリケーションが静的に Visual C++ ライブラリにリンクしている場合は、対応する DLL がユーザーのコンピューター上に存在する必要はありません。 ただし、静的リンクの場合、アプリケーション ファイルのサイズが大きくなることや、メンテナンスがより困難になる可能性があるなど、悪影響がいくつかあります。 詳細については、「[DLL の利点](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls)」を参照してください。

## <a name="packaging-and-redistributing"></a>パッケージ化と再配布

Visual C++ ライブラリは Dll としてパッケージ化され、C/C++ アプリケーションに必要なすべてのライブラリは、開発者のコンピューター上に Visual Studio によってインストールされます。 ただし、アプリケーションをユーザーに配置するときに、そのアプリケーションを実行するためにユーザーに対して Visual Studio のインストールを求めることは、ほとんどの場合は不可能です。 アプリケーションを正しく実行するために必要な Visual C++ の部分のみを再配布できることが重要です。

パッケージ化と再配布の詳細については、次のトピックを参照してください。

- [再配布する DLL の決定](../ide/determining-which-dlls-to-redistribute.md)。

- [配置方法の選択](../ide/choosing-a-deployment-method.md)。

- [ユニバーサル CRT の配置](universal-crt-deployment.md)。

配置例とトラブルシューティングに関する推奨事項については、以下を参照してください。

- [配置例](../ide/deployment-examples.md)。

- [C/C++ 分離アプリケーションおよび side-by-side アセンブリのトラブルシューティング](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。

## <a name="see-also"></a>関連項目

- [デスクトップ アプリケーションの配置](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Visual C++ アプリケーションの依存関係の理解](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)

