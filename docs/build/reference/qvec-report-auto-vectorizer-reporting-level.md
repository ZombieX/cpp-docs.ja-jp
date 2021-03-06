---
title: -Qvec-report (自動ベクター化レポート作成レベル) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7ee7ed9fbbe48477aecb51ca489fe2ad9609e41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408104"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (自動ベクター化レポート作成レベル)

コンパイラのレポート機能を有効に[自動ベクター化](../../parallel/auto-parallelization-and-auto-vectorization.md)し、コンパイル時に出力の情報メッセージのレベルを指定します。

## <a name="syntax"></a>構文

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Remarks

**/Qvec-レポート: 1**<br/>
ループのベクター化は、情報メッセージを出力します。

**/Qvec-レポート: 2**<br/>
For ループがベクター化して、for ループがベクター化されていない、理由コードと共にを情報メッセージを出力します。

理由コードとメッセージについては、次を参照してください。[ベクター化と並行化メッセージ](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)します。

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Visual Studio で/Qvec-report コンパイラ オプションを設定するには

1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。

1. **プロパティ ページ**ダイアログ ボックスで、 **C/C++**、**コマンド ライン**。

1. **追加オプション**ボックスに、入力`/Qvec-report:1`または`/Qvec-report:2`します。

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>/Qvec-report コンパイラ オプションをプログラムで設定するには

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> のコード例を使用してください。

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](../../build/reference/q-options-low-level-operations.md)<br/>
[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)<br/>
[ネイティブ コードでの並列プログラミング](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)