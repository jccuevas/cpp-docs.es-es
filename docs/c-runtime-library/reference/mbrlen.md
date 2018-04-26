---
title: mbrlen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
dev_langs:
- C++
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd71912412188f7e6c8df8e2cf744166ea928ee
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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
Puntero para el estado de desplazamiento actual del byte inicial de *str*.

## <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores:

|||
|-|-|
0|La siguiente *recuento* o menos bytes completan el carácter multibyte que representa el carácter nulo ancho.
1 a *recuento*, ambos inclusive|La siguiente *recuento* o menos bytes completan un carácter multibyte válido. El valor devuelto es el número de bytes que completan el carácter multibyte.
(size_t)(-2)|La siguiente *recuento* bytes contribuyen a un carácter multibyte incompleto pero potencialmente válido y los *recuento* bytes se han procesado.
(size_t)(-1)|Se produjo un error de codificación. La siguiente *recuento* o menos bytes no contribuyen a un carácter multibyte completo y válido. En este caso, **errno** se establece a EILSEQ y el estado de la conversión en *mbstate* no está especificado.

## <a name="remarks"></a>Comentarios

El **mbrlen** función inspecciona a lo sumo *recuento* bytes a partir del byte señalado por *str* para determinar el número de bytes que se necesitan para completar la siguiente carácter multibyte, incluidas las secuencias de desplazamiento. Es equivalente a la llamada `mbrtowc(NULL, str, count, &mbstate)` donde *mbstate* es cualquier un proporcionado por el usuario **mbstate_t** objeto o un objeto interno estático proporcionadas por la biblioteca.

El **mbrlen** función guarda y usa el estado de desplazamiento de un carácter multibyte incompleto en el *mbstate* parámetro. Esto proporciona **mbrlen** la capacidad de reinicio en medio de un carácter multibyte si es necesario, examinando a lo sumo *recuento* bytes. Si *mbstate* es un puntero nulo, **mbrlen** usa un elemento estático interno, **mbstate_t** objeto para almacenar el estado de desplazamiento. Dado que el fax interno **mbstate_t** objeto no es seguro para subprocesos, se recomienda siempre asignar y pasar su propio *mbstate* parámetro.

El **mbrlen** función difiere de [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) por su capacidad de reinicio. El estado de desplazamiento se almacena en *mbstate* para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe utilizar **wcsrlen** en lugar de **wcslen** si una llamada subsiguiente a **wcsrtombs** se utiliza en lugar de **wcstombs**.

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

Este ejemplo muestra cómo la interpretación de caracteres multibyte depende de la página de códigos actual y demuestra la capacidad de reanudación de **mbrlen**.

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
