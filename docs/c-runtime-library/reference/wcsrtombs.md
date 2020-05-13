---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: cad31f28c5542a96eae9f144344882b71806052a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910627"
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
Puntero a un objeto de estado de la conversión **mbstate_t** .

## <a name="return-value"></a>Valor devuelto

Devuelve el número de bytes convertidos correctamente, sin incluir el byte nulo de finalización (si lo hubiera), de lo contrario, -1 si se ha producido un error.

## <a name="remarks"></a>Observaciones

La función **wcsrtombs** convierte una cadena de caracteres anchos, comenzando en el estado de conversión especificado incluido en *mbstate*, de los valores a los que se señala indirectamente en *wcstr*, en la dirección de *mbstr*. La conversión continuará para cada carácter hasta que: después de que se encuentre un carácter ancho de terminación null, cuando se encuentre un carácter no correspondiente o cuando el siguiente carácter exceda el límite contenido en *Count*. Si **wcsrtombs** detecta el carácter nulo de caracteres anchos (L ' \ 0 ') antes o cuando se produce el *recuento* , lo convierte en un 0 de 8 bits y se detiene.

Por lo tanto, la cadena de caracteres multibyte en *mbstr* está terminada en NULL solo si **wcsrtombs** encuentra un carácter ancho nulo durante la conversión. Si las secuencias señaladas por *wcstr* y *mbstr* se superponen, el comportamiento de **wcsrtombs** es indefinido. **wcsrtombs** se ve afectado por la categoría LC_TYPE de la configuración regional actual.

La función **wcsrtombs** difiere de [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) por su reinicio. El estado de la conversión se almacena en *mbstate* para las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación usaría **wcsrlen** en lugar de **wcsnlen**, si se usara una llamada subsiguiente a **wcsrtombs** en lugar de **wcstombs**.

Si el argumento *mbstr* es **null**, **wcsrtombs** devuelve el tamaño necesario en bytes de la cadena de destino. Si *mbstate* es null, se utiliza el estado de conversión de **mbstate_t** interno. Si la secuencia de caracteres *WCHAR* no tiene una representación de caracteres multibyte correspondiente, se devuelve-1 y **errno** se establece en **EILSEQ**.

En C++, esta función tiene una sobrecarga de plantilla que invoca una contrapartida más nueva y segura de la función. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="exceptions"></a>Excepciones

La función **wcsrtombs** es segura para subprocesos siempre y cuando ninguna función del subproceso actual llame a **setlocale** mientras se ejecuta esta función y el valor de *mbstate* no sea NULL.

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

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
