---
title: 配置方法の選択 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 407972d9df042854ec1cd5a61964782422f359a6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433531"
---
# <a name="choosing-a-deployment-method"></a>配置方法の選択

Visual C++ アプリケーションを単体で使用できない場合や、コピー コマンドを使用して配置できない場合は、Windows インストーラーを使用して配置することをお勧めします。 Windows インストーラーでは、インストール、修復、およびアンインストールのほか、アプリケーション ファイル、依存関係、およびレジストリ エントリの分割不可能な更新もサポートされています。

> [!NOTE]
>  Visual C++ ネイティブ アプリケーションの [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) 配置は Visual Studio でも可能ですが、追加の手順が必要になります。 詳細については、「 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)」を参照してください。

## <a name="visual-c-libraries-are-shared-dlls"></a>Visual C++ ライブラリの共有 DLL

Visual Studio インストーラーでは、Visual C++ ライブラリが %windir%\system32\ ディレクトリにインストールされるため、このライブラリに依存する Visual C++ アプリケーションを開発する場合、そのアプリケーションは意図したとおりに実行されます。 ただし、Visual Studio がない可能性があるコンピューターにアプリケーションを配置する場合は、ライブラリがアプリケーションと共にそのコンピューターにインストールされているかどうかを確認することをお勧めします。

## <a name="redistributing-visual-c-libraries"></a>Visual C++ ライブラリの再配布

ご利用の配置に、再頒布用にライセンスされた任意のバージョンの Visual C++ ライブラリを再頒布できます。 配置する方法は 3 つあります。

- 再頒布可能パッケージを使用した集中配置。Visual C++ ライブラリが共有 DLL として %windir%\system32\\ にインストールされます  (このフォルダーにインストールするには管理者権限が必要です)。アプリケーションをターゲット コンピューターにインストールする前に、再頒布可能パッケージを実行するスクリプトまたはセットアップ プログラムを作成できます。 再頒布可能パッケージは、x86 プラットフォーム、x64 プラットフォーム、および ARM プラットフォーム (VCRedist_x86.exe、VCRedist_x64.exe、または VCRedist_arm.exe) で使用できます。 Visual Studio では、これらのパッケージは %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\ に含まれています。 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/p/?linkid=132793)からダウンロードすることもできます  (ダウンロード センターの検索ボックスを使用して、ご利用のアプリケーションと一致する "Visual C++ 再頒布可能パッケージ *Visual Studio バージョンと更新プログラム*" を検索します。 たとえば、Visual Studio 2015 更新プログラム 3 を使用してアプリケーションをビルドした場合は、"Visual C++ 再頒布可能パッケージ 2015 更新プログラム 3" を検索します)。再頒布可能パッケージの使用方法については、「[チュートリアル: Visual C++ 再頒布可能パッケージを使用した Visual C++ アプリケーションの配置](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)」を参照してください。

- マージ モジュールを使用した集中配置。各マージ モジュールによって特定の Visual C++ ライブラリが共有 DLL として %windir%\system32\\ にインストールされます  (このフォルダーにインストールするには管理者権限が必要です)。マージ モジュールは、アプリケーションの .msi インストーラー ファイルの一部になります。 Visual C++ の再頒布可能なマージ モジュールは、Visual Studio の \Program Files (x86)\Common Files\Merge Modules\\ に含まれています。 詳細については、「[マージ モジュールを使用した再配布](../ide/redistributing-components-by-using-merge-modules.md)」を参照してください。

- ローカル配置。Visual Studio インストール (通常は \Program Files (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\) から特定の Visual C++ DLL をコピーし、インストール先のコンピューターで、アプリケーションの実行可能ファイルと同じフォルダーにインストールします。 この配置方法を使用すると、管理者権限を持たないユーザーによるインストール、またはネットワーク共有から実行できるアプリケーションに対するインストールが可能です。

再頒布可能なマージ モジュールが使用されている配置で、管理者権限を持たないユーザーがインストールを実行すると、Visual C++ DLL はインストールされず、アプリケーションは実行されません。 また、ユーザー単位でのインストールを許可するマージ モジュールでビルドされたアプリケーション インストーラーでは、システムのすべてのユーザーに影響を及ぼす共有の場所にライブラリがインストールされます。 ローカル配置を使用すると、必要な Visual C++ DLL を特定のユーザーのアプリケーションのディレクトリに、他のユーザーに影響を与えることなくインストールできます。管理者権限も不要ですが、 これによりサービス性に問題が発生する可能性があるため、Visual C++ の再頒布可能 DLL のローカル配置はお勧めしません。

Visual C++ ライブラリの配置が不適切だと、そのライブラリに依存するアプリケーションの実行時に実行時エラーが発生する可能性があります。 オペレーティング システムでアプリケーションを読み込む場合、[LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792) に関するページに示されている検索順序が使用されます。

## <a name="dynamic-linking-is-better-than-static-linking"></a>動的リンクを静的リンクに優先させる

Visual C++ ライブラリを再配布する場合、静的リンクは使用しないことをお勧めします。 アプリケーションのパフォーマンスが静的リンクによって大きく向上することはほぼありませんが、サービスのコストは、ほとんどの場合、高くなります。 たとえば、セキュリティの強化によって更新されるライブラリに静的にリンクしているアプリケーションについて考えます。このアプリケーションは、再コンパイルして再配置しなければ、セキュリティ強化のメリットを得ることはできません。 代わりに、アプリケーションをライブラリに動的にリンクさせて、配置される場所でライブラリを更新できるようにすることをお勧めします。

## <a name="see-also"></a>参照

[デスクトップ アプリケーションの配置](../ide/deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[配置例](../ide/deployment-examples.md)