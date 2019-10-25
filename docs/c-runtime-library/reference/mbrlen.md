---
title: mbrlen
ms.date: 11/04/2016
api_name:
- mbrlen
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: c9559731f39db35e03f640bb30b9af3fff00cf66
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952505"
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

*str*<br/>
Puntero al siguiente byte que se va a inspeccionar en una cadena de caracteres multibyte.

*count*<br/>
El número máximo de bytes a inspeccionar.

*mbstate*<br/>
Puntero al estado de desplazamiento actual del byte inicial de *Str*.

## <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores:

|||
|-|-|
0|El siguiente *recuento* o menos bytes completan el carácter multibyte que representa el carácter nulo ancho.
1 para *contar*, ambos inclusive|El siguiente *recuento* o menos bytes completan un carácter multibyte válido. El valor devuelto es el número de bytes que completan el carácter multibyte.
(size_t)(-2)|El siguiente *recuento* de bytes contribuye a un carácter multibyte incompleto pero potencialmente válido, y se han procesado todos los bytes de *recuento* .
(size_t)(-1)|Se produjo un error de codificación. El siguiente *recuento* o menos bytes no contribuyen a un carácter multibyte completo y válido. En este caso, **errno** se establece en EILSEQ y el estado de la conversión en *mbstate* no se especifica.

## <a name="remarks"></a>Comentarios

La función **mbrlen** inspecciona como máximo los bytes de *recuento* a partir del byte señalado por *Str* para determinar el número de bytes necesarios para completar el siguiente carácter multibyte, incluidas las secuencias de desplazamiento. Es equivalente a la llamada `mbrtowc(NULL, str, count, &mbstate)` , donde *mbstate* es un objeto **mbstate_t** proporcionado por el usuario o un objeto interno estático proporcionado por la biblioteca.

La función **mbrlen** guarda y usa el estado de desplazamiento de un carácter multibyte incompleto en el parámetro *mbstate* . Esto da a **mbrlen** la capacidad de reiniciar en medio de un carácter multibyte si es necesario, examinando a lo sumo el *número* de bytes. Si *mbstate* es un puntero nulo, **mbrlen** usa un objeto **mbstate_t** interno estático para almacenar el estado de desplazamiento. Dado que el objeto **mbstate_t** interno no es seguro para subprocesos, se recomienda asignar siempre y pasar su propio parámetro *mbstate* .

La función **mbrlen** difiere de [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) por su reinicio. El estado de desplazamiento se almacena en *mbstate* para las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe usar **wcsrlen** en lugar de **wcslen** si se utiliza una llamada subsiguiente a **wcsrtombs** en lugar de **wcstombs**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|No aplicable|No aplicable|**mbrlen**|No aplicable|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
