---
title: getchar, getwchar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- getchar
- getwchar
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
- getwchar
- GetChar
dev_langs:
- C++
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c05fca568c8d69d34aa1386030eef3f2cb09f11
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getchar-getwchar"></a>getchar, getwchar

Lee un carácter de entrada estándar.

## <a name="syntax"></a>Sintaxis

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Valor devuelto

Devuelve el carácter leído. Para indicar un error de lectura o una condición de final de archivo, **getchar** devuelve **EOF**, y **getwchar** devuelve **WEOF**. Para **getchar**, use **ferror** o **feof** para comprobar si hay un error o de fin de archivo.

## <a name="remarks"></a>Comentarios

Cada rutina lee un solo carácter de **stdin** y aumenta el puntero de archivo asociado para que apunte al carácter siguiente. **GetChar** es el mismo que [_fgetchar](fgetc-fgetwc.md), pero se implementa como una función, como una macro.

Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos. Para obtener una versión que no sea de bloqueo, consulte [_getchar_nolock, _getwchar_nolock](getchar-nolock-getwchar-nolock.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**getchar**|**getchar**|**getwchar**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**getchar**|\<stdio.h>|
|**getwchar**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
