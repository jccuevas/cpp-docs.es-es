---
title: wcrtomb
ms.date: 11/04/2016
apiname:
- wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: a5fad3f41c7ed459a1af3fae7c6a5a85c867d5ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659256"
---
# <a name="wcrtomb"></a>wcrtomb

Convierte un carácter ancho en su representación de carácter multibyte. Hay disponible una versión más segura de esta función; vea [wcrtomb_s](wcrtomb-s.md).

## <a name="syntax"></a>Sintaxis

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*mbchar*<br/>
Carácter convertido multibyte resultante.

*wchar*<br/>
Carácter ancho que se va a convertir.

*mbstate*<br/>
Un puntero a un **mbstate_t** objeto.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes necesarios para representar el carácter multibyte convertido; si se produce un error, devuelve -1.

## <a name="remarks"></a>Comentarios

El **wcrtomb** función convierte un carácter ancho, comenzando en el estado de conversión especificado contenido en *mbstate*, desde el valor contenido en *wchar*, en el dirección representada por *mbchar*. El valor devuelto es el número de bytes necesarios para representar el carácter multibyte correspondiente, pero no devolverá más de **MB_CUR_MAX** bytes.

Si *mbstate* es null, interno **mbstate_t** objeto que contiene el estado de conversión de *mbchar* se utiliza. Si la secuencia de caracteres *wchar* no tiene un multibyte correspondiente representación de caracteres, se devuelve -1 y el **errno** está establecido en **EILSEQ**.

El **wcrtomb** función difiere de [wctomb, _wctomb_l](wctomb-wctomb-l.md) por su capacidad de reinicio. El estado de conversión se almacena en *mbstate* en las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría **wcsrlen** lugar **wcsnlen**, si una llamada subsiguiente a **wcsrtombs** se usaron en lugar de **wcstombs**.

En C++, esta función tiene una sobrecarga de plantilla que invoca a un homólogo más reciente y seguro de esta función. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Excepciones

El **wcrtomb** función es segura para subprocesos siempre y cuando ninguna función en el subproceso actual llame a **setlocale** mientras se está ejecutando esta función y mientras la *mbstate* es null.

## <a name="example"></a>Ejemplo

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
