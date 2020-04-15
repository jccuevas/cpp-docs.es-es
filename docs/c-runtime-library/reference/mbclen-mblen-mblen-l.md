---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Describe las funciones _mbclen, mblen, _mblen_l y _mbclen_l de microsoft C Runtime Library (CRT).
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341119"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

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

*C*\
Carácter multibyte.

*mbstr*\
Dirección de una secuencia de bytes de caracteres multibyte.

*Contar*\
Número de bytes que se va a comprobar.

*Configuración regional*\
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbclen** y **_mbclen_l** devuelven 1 o 2, según la longitud del carácter multibyte *c*. Las funciones siempre devuelven 1 para UTF-8, ya sea *que c* sea multibyte o no. No hay ningún retorno de error para **_mbclen**.

Si *mbstr* no es **NULL**, **mblen** y **_mblen_l** devuelven la longitud, en bytes, del carácter multibyte. Las funciones **mblen** y **_mblen_l** funcionan correctamente en UTF-8 y pueden devolver un valor entre 1 y 3. Cuando *mbstr* es **NULL** (o apunta al carácter nulo de caracteres anchos), **mblen** y **_mblen_l** devuelven 0. El objeto al que apunta *mbstr* debe formar un carácter multibyte válido dentro de los primeros caracteres de *recuento,* o **mblen** y **_mblen_l** devuelven -1.

## <a name="remarks"></a>Observaciones

La función **_mbclen** devuelve la longitud, en bytes, del carácter multibyte *c*. Si *c* no apunta al byte principal de un carácter multibyte (según lo determinado por una llamada implícita a [_ismbblead](ismbblead-ismbblead-l.md), el resultado de **_mbclen** es impredecible.

**mblen** devuelve la longitud en bytes de *mbstr* si es un carácter multibyte válido. También determina la validez de caracteres multibyte asociada a la página de códigos. **mblen** examina *el recuento* o menos bytes contenidos en *mbstr*, pero no más de **MB_CUR_MAX** bytes.

El valor de salida se ve afectado por la configuración de categoría **de LC_CTYPE** de la configuración regional. Las versiones de estas funciones sin el **sufijo _l** utilizan la configuración regional actual para este comportamiento dependiente de la configuración regional. Las **versiones con** _l sufijo stienen el mismo tipo, pero usan el parámetro de configuración regional pasado en su lugar. Para obtener más información, consulte [setlocale](setlocale-wsetlocale.md) y [Locale](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**y **_mbclen_l** son específicos de Microsoft, no parte de la biblioteca Estándar de C. No recomendamos que los use donde desee código portátil. Para la compatibilidad con Standard C, utilice **mblen** o **mbrlen** en su lugar.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)\
[Configuración regional](../../c-runtime-library/locale.md)\
[Interpretación de secuencias multibyte-carácter](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
