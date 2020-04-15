---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340992"
---
# <a name="mbrlen"></a>mbrlen

Determine el número de bytes que se necesitan para completar un carácter multibyte en la configuración regional actual, con capacidad de reinicio en medio de un carácter multibyte.

## <a name="syntax"></a>Sintaxis

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Puntero al siguiente byte que se va a inspeccionar en una cadena de caracteres multibyte.

*count*<br/>
El número máximo de bytes a inspeccionar.

*mbstate*<br/>
Puntero al estado de desplazamiento actual del byte inicial de *str*.

## <a name="return-value"></a>Valor devuelto

Uno de los valores siguientes:

|||
|-|-|
0|El siguiente *recuento* o menos bytes completan el carácter multibyte que representa el carácter nulo ancho.
1 a *contar,* incluido|El siguiente *recuento* o menos bytes completan un carácter multibyte válido. El valor devuelto es el número de bytes que completan el carácter multibyte.
(size_t)(-2)|Los bytes de *recuento* siguiente contribuyen a un carácter multibyte incompleto pero potencialmente válido y se han procesado todos los bytes de *recuento.*
(size_t)(-1)|Se produjo un error de codificación. El siguiente *recuento* o menos bytes no contribuyen a un carácter multibyte completo y válido. En este caso, **errno** se establece en EILSEQ y el estado de conversión en *mbstate* no se especifica.

## <a name="remarks"></a>Observaciones

La función **mbrlen inspecciona** a la mayoría de los bytes de *recuento* comenzando con el byte señalado por *str* para determinar el número de bytes necesarios para completar el siguiente carácter multibyte, incluidas las secuencias de desplazamiento. Es equivalente a `mbrtowc(NULL, str, count, &mbstate)` la llamada donde *mbstate* es un objeto **mbstate_t** proporcionado por el usuario o un objeto interno estático proporcionado por la biblioteca.

La función **mbrlen** guarda y utiliza el estado de desplazamiento de un carácter multibyte incompleto en el parámetro *mbstate.* Esto da **a mbrlen** la capacidad de reiniciar en medio de un carácter multibyte si es necesario, examinando a la mayoría de los bytes de *recuento.* Si *mbstate* es un puntero nulo, **mbrlen** utiliza un objeto **de mbstate_t** interno estático para almacenar el estado de desplazamiento. Dado que el objeto **de mbstate_t** interno no es seguro para subprocesos, se recomienda asignar y pasar siempre su propio parámetro *mbstate.*

La función **mbrlen** difiere de [_mbclen, mblen _mblen_l](mbclen-mblen-mblen-l.md) por su capacidad de reinicio. El estado de desplazamiento se almacena en *mbstate* para las llamadas posteriores a la misma u otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe utilizar **wcsrlen** en lugar de **wcslen** si se utiliza una llamada posterior a **wcsrtombs** en lugar de **wcstombs**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|no aplicable|no aplicable|**mbrlen**|no aplicable|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo la interpretación de caracteres multibyte depende de la página de códigos actual y se muestra la capacidad de reanudación de **mbrlen**.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
