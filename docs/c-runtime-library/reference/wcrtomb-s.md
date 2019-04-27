---
title: wcrtomb_s
ms.date: 11/04/2016
apiname:
- wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 7fe7fba861eecec562928cf381973f62a4db60fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155477"
---
# <a name="wcrtombs"></a>wcrtomb_s

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
El tamaño de la *mbchar* variable en bytes.

*wchar*<br/>
Carácter ancho que se va a convertir.

*mbstate*<br/>
Un puntero a un **mbstate_t** objeto.

## <a name="return-value"></a>Valor devuelto

Devuelve cero o un **errno** valor si se produce un error.

## <a name="remarks"></a>Comentarios

El **wcrtomb_s** función convierte un carácter ancho, comenzando en el estado de conversión especificado contenido en *mbstate*, desde el valor contenido en *wchar*, en el dirección representada por *mbchar*. El *pReturnValue* valor será el número de bytes convertidos, pero no más de **MB_CUR_MAX** bytes o -1 si se produjo un error.

Si *mbstate* es null, interno **mbstate_t** se usa el estado de la conversión. Si el carácter incluido en *wchar* no tiene un carácter multibyte correspondiente, el valor de *pReturnValue* será -1 y la función devolverá el **errno** valor de **EILSEQ**.

El **wcrtomb_s** función difiere de [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) por su capacidad de reinicio. El estado de conversión se almacena en *mbstate* en las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría **wcsrlen** lugar **wcslen**, si una llamada subsiguiente a **wcsrtombs_s** se usaron en lugar de **wcstombs_s**.

En C++, el uso de esta función se simplifica con las sobrecargas de plantilla; las sobrecargas pueden deducir automáticamente la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Excepciones

El **wcrtomb_s** función es segura para subprocesos siempre y cuando ninguna función en el subproceso actual llame a **setlocale** mientras se está ejecutando esta función y el *mbstate* es null.

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

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
