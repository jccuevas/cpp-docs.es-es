---
title: wcrtomb_s
ms.date: 4/2/2020
api_name:
- wcrtomb_s
- _o_wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 51985b008565cbe550065b85261b8beb53ed6f89
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915958"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Convierte un carácter ancho en su representación de carácter multibyte. Versión de [wcrtomb](wcrtomb.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
Devuelve el número de bytes escritos o -1 si se ha producido un error.

*mbchar*<br/>
Carácter convertido multibyte resultante.

*sizeOfmbchar*<br/>
Tamaño de la variable *mbchar* en bytes.

*WCHAR*<br/>
Carácter ancho que se va a convertir.

*mbstate*<br/>
Puntero a un objeto **mbstate_t** .

## <a name="return-value"></a>Valor devuelto

Devuelve cero o un valor **errno** si se produce un error.

## <a name="remarks"></a>Observaciones

La función **wcrtomb_s** convierte un carácter ancho, comenzando en el estado de conversión especificado incluido en *mbstate*, del valor contenido en *WCHAR*, en la dirección representada por *mbchar*. El valor de *pReturnValue* será el número de bytes convertidos, pero no más de **MB_CUR_MAX** bytes o-1 si se ha producido un error.

Si *mbstate* es null, se utiliza el estado de conversión de **mbstate_t** interno. Si el carácter contenido en *WCHAR* no tiene un carácter multibyte correspondiente, el valor de *pReturnValue* será-1 y la función devolverá el valor **errno** de **EILSEQ**.

La función **wcrtomb_s** difiere de [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) por su reinicio. El estado de la conversión se almacena en *mbstate* para las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría **wcsrlen** en lugar de **wcslen**, si se utiliza una llamada subsiguiente a **wcsrtombs_s** en lugar de **wcstombs_s**.

En C++, el uso de esta función se simplifica con las sobrecargas de plantilla; las sobrecargas pueden deducir automáticamente la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="exceptions"></a>Excepciones

La función **wcrtomb_s** es segura para subprocesos siempre y cuando ninguna función del subproceso actual llame a **setlocale** mientras se ejecuta esta función y el valor de *mbstate* sea NULL.

## <a name="example"></a>Ejemplo

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
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
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
