---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: 4107ae6cb6366fa8ad80251ce94ee35ca59501bd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910642"
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

*WCHAR*<br/>
Carácter ancho que se va a convertir.

*mbstate*<br/>
Puntero a un objeto **mbstate_t** .

## <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes necesarios para representar el carácter multibyte convertido; si se produce un error, devuelve -1.

## <a name="remarks"></a>Observaciones

La función **wcrtomb** convierte un carácter ancho, comenzando en el estado de conversión especificado incluido en *mbstate*, del valor contenido en *WCHAR*, en la dirección representada por *mbchar*. El valor devuelto es el número de bytes necesarios para representar el carácter multibyte correspondiente, pero no devolverá más de **MB_CUR_MAX** bytes.

Si *mbstate* es null, se utiliza el objeto de **mbstate_t** interno que contiene el estado de conversión de *mbchar* . Si la secuencia de caracteres *WCHAR* no tiene una representación de caracteres multibyte correspondiente, se devuelve-1 y **errno** se establece en **EILSEQ**.

La función **wcrtomb** difiere de [wctomb, _wctomb_l](wctomb-wctomb-l.md) por su reinicio. El estado de la conversión se almacena en *mbstate* para las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría **wcsrlen** en lugar de **wcsnlen**, si se usara una llamada subsiguiente a **wcsrtombs** en lugar de **wcstombs**.

En C++, esta función tiene una sobrecarga de plantilla que invoca a un homólogo más reciente y seguro de esta función. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="exceptions"></a>Excepciones

La función **wcrtomb** es segura para subprocesos siempre y cuando ninguna función del subproceso actual llame a **setlocale** mientras se está ejecutando esta función y mientras que el valor de *mbstate* es NULL.

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

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
