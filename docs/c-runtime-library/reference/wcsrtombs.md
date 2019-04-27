---
title: wcsrtombs
ms.date: 11/04/2016
apiname:
- wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: 46ef195ec4685c327c4b5951ec44e5c363214b59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155334"
---
# <a name="wcsrtombs"></a>wcsrtombs

Convierte una cadena de caracteres anchos en su representación de cadena de caracteres multibyte. Hay disponible una versión más segura de esta función; vea [wcsrtombs_s](wcsrtombs-s.md).

## <a name="syntax"></a>Sintaxis

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*mbstr*<br/>
Ubicación de la dirección de la cadena de caracteres multibyte convertida resultante.

*wcstr*<br/>
Indirectamente apunta a la ubicación de la cadena de caracteres anchos que se va a convertir.

*count*<br/>
Número de caracteres que se van a convertir.

*mbstate*<br/>
Un puntero a un **mbstate_t** objeto de estado de conversión.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes convertidos correctamente, sin incluir el byte nulo de finalización (si lo hubiera), de lo contrario, -1 si se ha producido un error.

## <a name="remarks"></a>Comentarios

El **wcsrtombs** función convierte una cadena de caracteres anchos, comenzando en el estado de conversión especificado contenido en *mbstate*, de los valores indirectos que señala en *wcstr*, en la dirección de *mbstr*. La conversión continuará para cada carácter hasta que: después de encontrar un nulo de finalización de caracteres anchos, cuando se encuentra un carácter no correspondiente o cuando excede el límite de contenido en el siguiente carácter *recuento*. Si **wcsrtombs** encuentra el carácter nulo de caracteres anchos (L '\0') antes o al *recuento* se produce, convierte en un 0 de 8 bits y se detiene.

Por lo tanto, la cadena de caracteres multibyte en *mbstr* está terminada en null solo si **wcsrtombs** encuentra un carácter ancho nulo durante la conversión. Si las secuencias señaladas por *wcstr* y *mbstr* se superponen, el comportamiento de **wcsrtombs** es indefinido. **wcsrtombs** se ve afectado por la categoría LC_TYPE de la configuración regional actual.

El **wcsrtombs** función difiere de [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) por su capacidad de reinicio. El estado de conversión se almacena en *mbstate* en las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación usaría **wcsrlen** lugar **wcsnlen**, si una llamada subsiguiente a **wcsrtombs** se usaron en lugar de **wcstombs**.

Si el *mbstr* argumento es **NULL**, **wcsrtombs** devuelve el tamaño necesario en bytes de la cadena de destino. Si *mbstate* es null, interno **mbstate_t** se usa el estado de la conversión. Si la secuencia de caracteres *wchar* no tiene un multibyte correspondiente representación de caracteres, se devuelve -1 y el **errno** está establecido en **EILSEQ**.

En C++, esta función tiene una sobrecarga de plantilla que invoca una contrapartida más nueva y segura de la función. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Excepciones

El **wcsrtombs** función es segura para subprocesos siempre y cuando ninguna función en el subproceso actual llame a **setlocale** mientras se está ejecutando esta función y el *mbstate* no es null.

## <a name="example"></a>Ejemplo

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
