---
title: wctob
ms.date: 11/04/2016
apiname:
- wctob
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
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 9c977bc204f4c9428a4aae09300269b1ed82d53e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498956"
---
# <a name="wctob"></a>wctob

Determina si un carácter ancho se corresponde con un carácter multibyte y devuelve su representación de carácter multibyte.

## <a name="syntax"></a>Sintaxis

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parámetros

*wchar*<br/>
Valor que se va a traducir.

## <a name="return-value"></a>Valor devuelto

Si **wctob** convierte correctamente un carácter ancho, devuelve su representación de caracteres multibyte, solo si el carácter multibyte tiene una longitud exacta de un byte. Si **wctob** encuentra un carácter ancho que no se puede convertir en un carácter multibyte o el carácter multibyte no tiene exactamente un byte de longitud, devuelve-1.

## <a name="remarks"></a>Comentarios

La función **wctob** convierte un carácter ancho incluido en *WCHAR* en el carácter multibyte correspondiente pasado por el valor devuelto **int** , si el carácter multibyte tiene una longitud exacta de un byte.

Si **wctob** no tuvo éxito y no se encontró ningún carácter multibyte correspondiente, la función establece **errno** en **EILSEQ** y devuelve-1.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa muestra el comportamiento de la función **wcstombs** .

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
