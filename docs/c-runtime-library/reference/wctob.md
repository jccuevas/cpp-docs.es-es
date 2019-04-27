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
ms.openlocfilehash: 1d9dca16ca905afbc94d912a8083017ba9cc84e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188537"
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

Si **wctob** convierte correctamente un carácter ancho, devuelve su representación de carácter multibyte únicamente si el carácter multibyte es la longitud de exactamente un byte. Si **wctob** encuentra un carácter ancho que no se puede convertir en un carácter multibyte o carácter multibyte no es exactamente un byte de largo, devuelve -1.

## <a name="remarks"></a>Comentarios

El **wctob** función convierte un carácter ancho incluido en *wchar* en el carácter multibyte correspondiente pasado por la devolución **int** valor, si el multibyte carácter es la longitud de exactamente un byte.

Si **wctob** se realizó correctamente y no se encontró ningún carácter multibyte correspondiente, la función establece **errno** a **EILSEQ** y devuelve -1.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa muestra el comportamiento de la **wcstombs** función.

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
