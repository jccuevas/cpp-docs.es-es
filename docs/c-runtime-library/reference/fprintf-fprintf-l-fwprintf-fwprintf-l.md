---
title: fprintf, _fprintf_l, fwprintf, _fwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fwprintf
- fprintf
- _fprintf_l
- _fwprintf_l
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
apitype: DLLExport
f1_keywords:
- fprintf
- fwprintf
- _ftprintf
dev_langs:
- C++
helpviewer_keywords:
- _fwprintf_l function
- fprintf function
- fprintf_l function
- _fprintf_l function
- _ftprintf function
- fwprintf function
- ftprintf_l function
- ftprintf function
- _ftprintf_l function
- print formatted data to streams
- fwprintf_l function
ms.assetid: 34a87e1c-6e4d-4d48-a611-58314dd4dc4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7578a8a8c2bef7fe68e9a08ae987ac7c1609cb5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fprintf-fprintfl-fwprintf-fwprintfl"></a>fprintf, _fprintf_l, fwprintf, _fwprintf_l

Imprima datos con formato en una secuencia. Hay disponibles versiones más seguras de estas funciones; consulte [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
int fprintf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fprintf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwprintf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwprintf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parámetros

*Secuencia*<br/>
Puntero a la estructura **FILE**.

*format*<br/>
Cadena de control de formato.

*Argumento*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**fprintf** devuelve el número de bytes escritos. **fwprintf** devuelve el número de caracteres anchos que se escriben. Cada una de estas funciones devuelve un valor negativo cuando se produce un error de salida. Si *flujo* o *formato* es **NULL**, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven -1 y establecen **errno** a **EINVAL**. No se comprueba la cadena de formato de caracteres de formato válidos tal cual al usar **fprintf_s** o **fwprintf_s**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

**fprintf** da formato e imprime una serie de caracteres y valores a la salida de *flujo*. Cada función *argumento* (si existe) se convierte y sale según la especificación de formato correspondiente de *formato*. Para **fprintf**, *formato* argumento tiene la misma sintaxis y el uso que tiene en **printf**.

**fwprintf** es una versión con caracteres anchos de **fprintf**; en **fwprintf**, *formato* es una cadena de caracteres anchos. Estas funciones se comportan igual si el flujo se abre en modo ANSI. **fprintf** no admite actualmente la salida en un flujo UNICODE.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf**|**fprintf**|**fprintf**|**fwprintf**|
|**_ftprintf_l**|**_fprintf_l**|**_fprintf_l**|**_fwprintf_l**|

Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fprintf**, **_fprintf_l**|\<stdio.h>|
|**fwprintf**, **_fwprintf_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fprintf.c
/* This program uses fprintf to format various
* data and print it to the file named FPRINTF.OUT. It
* then displays FPRINTF.OUT on the screen using the system
* function to invoke the operating-system TYPE command.
*/

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf.out", "w" );
   fprintf( stream, "%s%c", s, c );
   fprintf( stream, "%d\n", i );
   fprintf( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[Sintaxis de especificación de formato: printf y wprintf (funciones)](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
