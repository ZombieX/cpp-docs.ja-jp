---
title: /(マイ コードのみのデバッグ) JMC |Microsoft Docs
ms.custom: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /JMC
dev_langs:
- C++
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1da60b43bd151a776278b51a5ee8a22de7ef3b4c
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "40242872"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (マイ コードのみのデバッグ)

ネイティブのコンパイラ サポートを指定*マイ コードのみ*Visual Studio デバッガーでデバッグします。 このオプションは、Visual Studio をステップ オーバー、システム、フレームワーク、ライブラリ、およびその他の非ユーザー呼び出しと呼び出し履歴 ウィンドウでそれらの呼び出しを折りたたむことを許可するユーザー設定をサポートします。 **/JMC**コンパイラ オプションは Visual Studio 2017 バージョン 15.8 以降を使用します。

## <a name="syntax"></a>構文

> **/JMC**\[**-**]

## <a name="remarks"></a>Remarks

Visual Studio[マイ コードのみ](/visualstudio/debugger/just-my-code)設定は、Visual Studio デバッガーをステップ オーバー、システム、フレームワーク、ライブラリ、およびその他の非ユーザー呼び出しかどうかを指定します。 **/JMC**コンパイラ オプション、ネイティブ C++ コードでマイ コードのみのデバッグのサポートを有効にします。 ときに **/JMC**が有効にすると、コンパイラは、ヘルパー関数の呼び出しを挿入`__CheckForDebuggerJustMyCode`、関数プロローグにします。 ヘルパー関数は、Visual Studio デバッガーの マイ コードのみのステップの操作をサポートするフックを提供します。 メニュー バーで、Visual Studio デバッガーでマイ コードのみを有効にする次のように選択します**ツール** > **オプション**、でのオプションを設定および**デバッグ** > 。**全般** > **マイ コードのみを有効にする**します。

**/JMC**オプションは、コード リンクに、C ランタイム ライブラリ (CRT) を提供していることが必要です、`__CheckForDebuggerJustMyCode`ヘルパー関数。 プロジェクトが、CRT にリンクしていない場合、リンカー エラーが発生**LNK2019: 未解決の外部シンボル __CheckForDebuggerJustMyCode**します。 このエラーを解決するのには、CRT にリンクまたはのいずれかを無効にする、 **/JMC**オプション。

既定で、 **/JMC**コンパイラ オプションはオフです。 ただし、このオプションを Visual Studio 2017 バージョン 15.8 以降は、ほとんどの Visual Studio プロジェクト テンプレートで有効です。 このオプションを明示的に無効にするには、 **/JMC-** コマンド ライン オプション。 Visual Studio でプロジェクトのプロパティ ページ ダイアログ ボックスを開くし、変更、**サポートだけマイ コードのデバッグ**プロパティ、**構成プロパティ** > **C/C++** > **全般**プロパティ ページを**いいえ**します。

詳細については、次を参照してください[マイ コードのみを C++](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code)で[Visual Studio での マイ コードのみを使用してユーザー コードのみをデバッグするかどうかを指定](/visualstudio/debugger/just-my-code)、および Visual c Team Blog post[発表 C++ マイ コードのみ。Visual Studio でのステップ実行](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **C/C++** > **全般**プロパティ ページ。

1. 変更、**サポートだけマイ コードのデバッグ**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)<br/>
