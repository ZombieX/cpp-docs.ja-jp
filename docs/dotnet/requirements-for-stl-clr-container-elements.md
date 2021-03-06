---
title: STL/CLR コンテナー要素の要件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fcba36fdf280cef31efb9a84288475fcbb82b291
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400427"
---
# <a name="requirements-for-stlclr-container-elements"></a>STL/CLR コンテナー要素の要件

STL/CLR コンテナーに挿入されたすべての参照型が必要には、少なくとも次の要素です。

- 公開コピー コンス トラクターです。

- パブリックの代入演算子です。

- パブリック デストラクターです。

さらなどの連想コンテナー[設定](../dotnet/set-stl-clr.md)と[マップ](../dotnet/map-stl-clr.md)はパブリックの比較演算子が定義されている必要があります`operator<`既定。 コンテナーの操作の一部は、パブリックの既定のコンス トラクターとパブリックな等価演算子を定義する必要もがあります。

参照型、値型およびハンドルが参照するように、連想コンテナーに挿入する型で必要があります、比較演算子など`operator<`定義します。 パブリックのコピー コンス トラクターをパブリックの代入演算子、およびパブリック デストラクターの要件は、値の型またはハンドル型を参照するには存在しません。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)