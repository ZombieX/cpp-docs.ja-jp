---
title: wctomb_s、_wctomb_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wctomb_s_l
- wctomb_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5bdc05f903c1313d4844be8d5fc4fa619505670
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195120"
---
# <a name="wctombs-wctombsl"></a>wctomb_s、_wctomb_s_l

ワイド文字を対応するマルチバイト文字に変換します。 「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [wctomb、_wctomb_l](wctomb-wctomb-l.md) です。

## <a name="syntax"></a>構文

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*pRetValue*<br/>
バイト数、または結果を示すコード。

*mbchar*<br/>
マルチバイト文字のアドレス。

*sizeInBytes*<br/>
バッファーのサイズ*mbchar*します。

*wchar*<br/>
ワイド文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

エラー条件

|*mbchar*|*sizeInBytes*|戻り値|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|変更されない|
|任意|>**INT_MAX**|**EINVAL**|変更されない|
|任意|小さすぎる|**EINVAL**|変更されない|

上記のいずれかのエラー条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 続けるには、実行が許可された場合**wctomb**返します**EINVAL**設定と**errno**に**EINVAL**します。

## <a name="remarks"></a>Remarks

**Wctomb_s**関数に変換しますその*wchar*を対応するマルチバイト文字の引数で結果を格納および*mbchar*します。 任意のプログラムの任意のポイントからこの関数を呼び出すことができます。

場合**wctomb_s**ワイド文字に変換をマルチバイト文字の場合は、バイト数が置かれる (よりも大きくなることはありません**MB_CUR_MAX**)によって示される整数に、ワイド文字*pRetValue*します。 場合*wchar*ワイド文字の null 文字 (L '\0') は、 **wctomb_s**塗りつぶします*pRetValue* 1。 場合、ターゲット ポインター *mbchar*は**NULL**、 **wctomb_s**に 0 を入れ*pRetValue*します。 現在のロケールで変換が不可能な場合**wctomb_s**に-1 を入れ*pRetValue*します。

**wctomb_s**ロケールに依存する情報の現在のロケールを使用 **_wctomb_s_l**代わりに渡されたロケールを使用すると同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムの動作を示しています、 **wctomb**関数。

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
