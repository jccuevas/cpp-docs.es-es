---
title: _mbclen, mblen, _mblen_l, _mbclen_l
ms.date: 01/22/2019
apiname:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: b7888b0b8c87a632dcbb63f54ade11080c7a309a
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702965"
---
# <a name="mbclen-mblen-mblenl-mbclenl"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Obtiene la longitud y determina la validez de un carácter multibyte.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter multibyte.

*mbstr*<br/>
Dirección de una secuencia de bytes de caracteres multibyte.

*count*<br/>
Número de bytes que se va a comprobar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbclen** devuelve 1 o 2, según si el carácter multibyte *c* es 1 o 2 bytes. No hay ningún error devuelto para **_mbclen**. Si *mbstr* no **NULL**, **mblen** devuelve la longitud, en bytes, del carácter multibyte. Si *mbstr* es **NULL** o señala al carácter null de caracteres anchos, **mblen** devuelve 0. Cuando el objeto que *mbstr* puntos que no forman un carácter multibyte válido en los primeros *recuento* caracteres, **mblen** devuelve -1.

## <a name="remarks"></a>Comentarios

El **_mbclen** función devuelve la longitud, en bytes, del carácter multibyte *c*. Si *c* no señala al byte inicial de un carácter multibyte determinado por una llamada implícita a **_ismbblead**, el resultado de **_mbclen** es imprevisible.

**mblen** devuelve la longitud en bytes de *mbstr* si es un carácter multibyte válido y determina la validez del carácter multibyte asociada con la página de códigos. **mblen** examina *recuento* bytes o menos en *mbstr*, pero no más de **MB_CUR_MAX** bytes.

El valor de salida se ve afectado por la **LC_CTYPE** valor de la categoría de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el **_l** sufijo usar la configuración regional actual para este comportamiento dependiente de la configuración regional. El **_l** versiones con sufijo comportan del mismo, pero usan el parámetro locale pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Se asigna a una macro o una función insertada|**_mbclen**|Se asigna a una macro o una función insertada|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
