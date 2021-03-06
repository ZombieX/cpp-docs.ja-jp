---
title: -vmm では、-vms、-vmv (General Purpose 表現) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cd0fb1eae8638f91ad97aec2ef24e0a578e7d7a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385548"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm、/vms、/vmv (通常の最適化)

ときに使用される[/vmb、/vmg () を処理形式](../../build/reference/vmb-vmg-representation-method.md)として選択されて、[表現メソッド](../../build/reference/vmb-vmg-representation-method.md)します。 これらのオプションは、not まだ検出クラス定義の継承モデルを示します。

## <a name="syntax"></a>構文

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>Remarks

これらのオプションの説明を次の表に示します。

|オプション|説明|
|------------|-----------------|
|**/vmm**|多重継承を使用するいずれかを指定するには、クラスのメンバーへのポインターの最も一般的な表現を指定します。<br /><br /> 対応する[継承キーワード](../../cpp/inheritance-keywords.md)への引数と[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)は**multiple_inheritance**します。<br /><br /> この表現は、単一継承した場合よりも大きくなります。<br /><br /> メンバーへのポインターが宣言されているクラス定義の継承モデルが仮想の場合、コンパイラはエラーを生成します。|
|**/vms**|いない継承または単一継承のいずれかを使用していずれかを指定するには、クラスのメンバーへのポインターの最も一般的な表現を指定します。<br /><br /> 対応する[継承キーワード](../../cpp/inheritance-keywords.md)への引数と[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)は**single_inheritance**します。<br /><br /> これは、クラスのメンバーへのポインターの最小サイズの表現です。<br /><br /> メンバーへのポインターが宣言されているクラス定義の継承モデルが複数ある場合または仮想の場合、コンパイラ エラーが発生します。|
|**/vmv**|仮想継承を使用するいずれかを指定するには、クラスのメンバーへのポインターの最も一般的な表現を指定します。 ありません、エラーが発生し、既定値です。<br /><br /> 対応する[継承キーワード](../../cpp/inheritance-keywords.md)への引数と[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)は**virtual_inheritance**します。<br /><br /> このオプションは、大きいサイズのポインターおよびその他のオプションよりもポインターを解釈するコードを追加が必要です。|

これらの継承モデル オプションのいずれかを指定すると、そのモデルは、クラス後の継承の種類や前に、またはにポインターを宣言するかどうかに関係なく、クラス メンバーへのすべてのポインターに使用されます。 そのため、常に単一継承のクラスを使用する場合はサイズを小さくコードでコンパイルする **/vms**ただし、(ただし、最大のデータ表現) の最も一般的なケースを使用する場合は、コンパイル **。/vmv**します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/vmb、/vmg (処理形式)](../../build/reference/vmb-vmg-representation-method.md)<br/>
[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)