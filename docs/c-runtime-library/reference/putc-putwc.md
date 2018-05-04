---
title: putc, putwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 931a1a586f46327dd800ca5e1b2ef9a0b22f469d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="putc-putwc"></a>putc, putwc

Escribe un carácter en un flujo.

## <a name="syntax"></a>Sintaxis

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que se va a escribir.

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Devuelve el carácter escrito. Para indicar un error o una condición de final de archivo, **putc** y **putchar** devolver ** EOF`; **putwc` y **putwchar** devolver **WEOF**. Para las cuatro rutinas, use [ferror](ferror.md) o [feof](feof.md) para comprobar si hay un error o una condición de final de archivo. Si pasa un puntero nulo para *flujo*, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** o **WEOF** y establecer **errno** a **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

El **putc** rutina escribe el carácter único *c* a la salida de *flujo* en la posición actual. Cualquier entero puede pasarse a **putc**, sino que solo los 8 bits inferiores se escriben. El **putchar** es idéntica a la rutina **putc (** * c ***, stdout)**. Para cada rutina, si se produce un error de lectura, se establece el indicador de error para el flujo. **putc** y **putchar** son similares a **fputc** y **_fputchar**, respectivamente, pero se implementan como funciones y como macros (vea [ Elegir entre funciones y Macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** y **putwchar** son versiones de caracteres anchos de **putc** y **putchar**, respectivamente. **putwc** y **putc** se comportan exactamente igual si el flujo se abre en modo ANSI. **putc** no admite actualmente la salida en un flujo UNICODE.

Las versiones que tienen el sufijo **_nolock** son idénticas, salvo que no están protegidas contra las interferencias de otros subprocesos. Para obtener más información, vea **_putc_nolock, _putwc_nolock**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>Salida

```Output
This is the line of output
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
