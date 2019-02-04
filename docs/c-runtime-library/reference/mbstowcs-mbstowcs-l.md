---
title: mbstowcs, _mbstowcs_l
ms.date: 11/04/2016
apiname:
- mbstowcs
- _mbstowcs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: 18e86ce359ff3b384ff8ef7dd5977d3be8d4785f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702770"
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs, _mbstowcs_l

Convertir una secuencia de caracteres multibyte en una secuencia correspondiente de caracteres anchos. Hay disponibles versiones más seguras de estas funciones; vea [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
size_t mbstowcs(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count
);
size_t _mbstowcs_l(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t mbstowcs(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
size_t _mbstowcs_l(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*wcstr*<br/>
Dirección de una secuencia de caracteres anchos.

*mbstr*<br/>
Dirección de una secuencia de caracteres multibyte terminados en nulo.

*count*<br/>
El número máximo de caracteres multibyte que se van a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Si **mbstowcs** convierte correctamente la cadena de origen, devuelve el número de caracteres multibyte convertidos. Si el *wcstr* argumento es **NULL**, la función devuelve el tamaño necesario (en caracteres anchos) de la cadena de destino. Si **mbstowcs** encuentra un carácter multibyte no válido, devuelve -1. Si el valor devuelto es *recuento*, la cadena de caracteres anchos no está terminada en null.

> [!IMPORTANT]
> Asegúrese de que *wcstr* y *mbstr* no se superponen y que *recuento* refleja correctamente el número de caracteres multibyte a convertir.

## <a name="remarks"></a>Comentarios

El **mbstowcs** función convierte hasta un número máximo de *recuento* caracteres multibyte señalados por *mbstr* en una cadena de caracteres anchos correspondientes que están determinado por la configuración regional actual. Almacena la cadena de caracteres anchos resultante en la dirección representada por *wcstr*. El resultado es similar a una serie de llamadas a [mbtowc](mbtowc-mbtowc-l.md). Si **mbstowcs** encuentra el carácter nulo de un byte ('\0') antes o al *recuento* se produce, convierten el carácter nulo en un carácter nulo de caracteres anchos (L '\0') y se detiene. Por tanto, la cadena de caracteres anchos en *wcstr* está terminada en null solo si se encuentra un carácter nulo durante la conversión. Si las secuencias señaladas por *wcstr* y *mbstr* se superponen, el comportamiento es indefinido.

Si el *wcstr* argumento es **NULL**, **mbstowcs** devuelve el número de caracteres anchos que daría como resultado de la conversión, sin incluir un terminador nulo. La cadena de origen debe terminar en nulo para que se devuelva el valor correcto. Si necesita que la cadena de caracteres anchos resultante termine en nulo, agregue uno al valor devuelto.

Si el *mbstr* argumento es **NULL**, o si *recuento* es > **INT_MAX**, se invoca el controlador de parámetros no válidos, como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, errno se establece en **EINVAL** y la función devuelve -1.

**mbstowcs** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; **_mbstowcs_l** es idéntico, salvo que usa la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbstowcs**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_mbstowcs.c
// compile with: /W3
// illustrates the behavior of the mbstowcs function

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main( void )
{
    size_t size;
    int nChar = 2; // number of characters to convert
    int requiredSize;

    unsigned char    *pmbnull  = NULL;
    unsigned char    *pmbhello = NULL;
    char* localeInfo;

    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters
    wchar_t *pwc;

    /* Enable the Japanese locale and codepage */
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");
    printf("Locale information set to %s\n", localeInfo);

    printf( "Convert to multibyte string:\n" );

    requiredSize = wcstombs( NULL, pwchello, 0); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    printf("   Required Size: %d\n", requiredSize);

    /* Add one to leave room for the null terminator. */
    pmbhello = (unsigned char *)malloc( requiredSize + 1);
    if (! pmbhello)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    if (size == (size_t) (-1))
    {
        printf("Couldn't convert string. Code page 932 may"
                " not be available.\n");
        return 1;
    }
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

    printf( "Convert back to wide-character string:\n" );

    /* Assume we don't know the length of the multibyte string.
     Get the required size in characters, and allocate enough space. */

    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996
    /* Add one to leave room for the null terminator */
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));
    if (! pwc)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996
    if (size == (size_t) (-1))
    {
       printf("Couldn't convert string--invalid multibyte character.\n");
    }
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );
    free(pwc);
    free(pmbhello);
}
```

```Output
Locale information set to Japanese_Japan.932
Convert to multibyte string:
   Required Size: 4
   Number of bytes written to multibyte string: 4
   Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1
   Codepage 932 uses 0x81 to 0x9f as lead bytes.

Convert back to wide-character string:
   Characters converted: 2
   Hex value of first 2 wide characters: 0x3042 0x3043
```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
