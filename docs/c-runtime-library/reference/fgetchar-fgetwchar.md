---
title: _fgetchar, _fgetwchar
ms.date: 11/04/2016
apiname:
- _fgetchar
- _fgetwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: c74618fa0be5392062d13618ff73e2ef45bf7c2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453790"
---
# <a name="fgetchar-fgetwchar"></a>_fgetchar, _fgetwchar

Lee un carácter de **stdin**.

## <a name="syntax"></a>Sintaxis

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Valor devuelto

**\_fgetchar** devuelve el carácter leído como un **int** o devuelve `EOF` para indicar un error o el final del archivo. **\_fgetwchar** devuelve, como un [wint_t](../../c-runtime-library/standard-types.md), el carácter ancho correspondiente al carácter leído, o bien devuelve `WEOF` para indicar un error o el final del archivo. Para ambas funciones, use **feof** o **ferror** para distinguir entre un error y una condición de final de archivo.

## <a name="remarks"></a>Comentarios

Estas funciones leen un solo carácter de **stdin**. A continuación, la función aumenta el puntero de archivo asociado (si está definido) para señalar al carácter siguiente. Si el flujo está al final del archivo, se establece la marca de fin de archivo para el flujo.

**_fgetchar** es equivalente a `fgetc( stdin )`. También es equivalente a **getchar**, pero implementado solo como una función, en lugar de una función y una macro. **_fgetwchar** es la versión de caracteres anchos de **_fgetchar**.

Estas funciones no son compatibles con el estándar ANSI.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Identificadores estándar de flujo que están asociados con la consola —**stdin**, **stdout**, y **stderr**: se debe redireccionar antes las funciones de tiempo de ejecución de C puedan usarlos en aplicaciones para UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
