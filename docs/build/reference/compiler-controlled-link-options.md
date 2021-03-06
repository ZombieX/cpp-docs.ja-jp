---
title: コンパイラで制御される LINK オプション |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee952fe5152d98aa33c4ef7e98f8a2eb3ef077be
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726428"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

CL コンパイラは、/c オプションを指定しない限り、リンクを自動的に呼び出します。 CL は、いくつかのコマンド ライン オプションと引数をリンカーに制御を提供します。 次の表では、リンクに影響を与える CL の機能をまとめたものです。

|CL の仕様|CL アクション リンクに影響を与える|
|----------------------|---------------------------------|
|.C、.cxx、.cpp、または .def 以外の任意のファイル名拡張子|リンクへの入力としてファイル名を渡します|
|*ファイル名*.def|/DEF を渡します*filename*.def。|
|/F*数*|パス/STACK:*数*|
|/Fd*ファイル名*|/PDB を渡します*ファイル名。*|
|/Fe*ファイル名*|渡します/アウト:*ファイル名*|
|/Fm*ファイル名*|パス/MAP:*ファイル名*|
|/Gy|パッケージ化された関数 (Comdat); を作成します。関数レベルのリンクを可能に|
|/LD|/DLL を渡します|
|/LDd|/DLL を渡します|
|/link|コマンドラインの残りの部分を LINK に渡します。|
|/MD、/MT または|既定のライブラリ名を .obj ファイル配置します。|
|/Mdd または/MTd|既定のライブラリ名は、.obj ファイルに配置します。 シンボルを定義 **_DEBUG**|
|/nologo|/NOLOGO を渡します|
|/Zd|/DEBUG のパス|
|/Zi または/Z7|/DEBUG のパス|
|/Zl|.Obj ファイルから既定のライブラリ名を省略します。|

詳細については、「[コンパイラ オプション](../../build/reference/compiler-options.md)」を参照してください。

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)