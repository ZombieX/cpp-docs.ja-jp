---
title: オーバーライド指定子 (C +/cli および C++/cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0620bc7045dcb312667cfdfe670e1f19b0545cf2
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327465"
---
# <a name="override-specifiers--ccli-and-ccx"></a>オーバーライド指定子 (C +/cli および C++/cli CX)

*オーバーライド指定子*継承された型を変更し、継承された型のメンバーの派生型で動作します。

## <a name="all-runtimes"></a>すべてのランタイム

### <a name="remarks"></a>Remarks

オーバーライド指定子の詳細については、以下を参照してください。

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [new (新規スロット vtable の)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [オーバーライド指定子とネイティブ コンパイル](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**抽象**と**シール**もで有効な型の宣言、機能しないようにオーバーライド指定子。

基底クラスの関数を明示的にオーバーライドする方法の詳細については、次を参照してください。[明示的なオーバーライド](../windows/explicit-overrides-cpp-component-extensions.md)します。

## <a name="windows-runtime"></a>Windows ランタイム

(この言語機能には Windows ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

(この言語機能には共通言語ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>必要条件

コンパイラ オプション: `/clr`

## <a name="see-also"></a>関連項目

[Component Extensions for .NET と UWP](../windows/component-extensions-for-runtime-platforms.md)