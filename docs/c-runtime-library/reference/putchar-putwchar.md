---
title: putchar, putwchar
ms.date: 4/2/2020
api_name:
- putchar
- putwchar
- _o_putchar
- _o_putwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putchar
- putwchar
- _puttchar
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
ms.openlocfilehash: 09ad53a7f4e953da05d7eafd6662bf250731b5d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333128"
---
# <a name="putchar-putwchar"></a>putchar, putwchar

Escribe un carácter en **stdout**.

## <a name="syntax"></a>Sintaxis

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Carácter que se va a escribir.

## <a name="return-value"></a>Valor devuelto

Devuelve el carácter escrito. Para indicar un error o una condición de fin de archivo, **putc** y **putchar** devuelven **EOF**; **putwc** y **putwchar** regresan **WEOF**. Para las cuatro rutinas, use [ferror](ferror.md) o [feof](feof.md) para comprobar si hay un error o una condición de final de archivo. Si se pasa un puntero nulo para *stream*, estas funciones generan una excepción de parámetro no válida, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven **EOF** o **WEOF** y establecen **errno** en **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Observaciones

La rutina **putc** escribe el carácter único *c* en la *secuencia* de salida en la posición actual. Cualquier entero se puede pasar a **putc**, pero solo se escriben los 8 bits inferiores. La rutina **putchar** `putc( c, stdout )`es idéntica a . Para cada rutina, si se produce un error de lectura, se establece el indicador de error para el flujo. **putc** y **putchar** son similares a **fputc** y **_fputchar**, respectivamente, pero se implementan como funciones y como macros (consulte [Elegir entre funciones y macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** y **putwchar** son versiones de caracteres anchos de **putc** y **putchar**, respectivamente.

Las versiones que tienen el sufijo **_nolock** son idénticas, salvo que no están protegidas contra las interferencias de otros subprocesos. Pueden ser más rápidas, porque no incurren en la sobrecarga de bloquear otros subprocesos. Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la Plataforma universal de Windows (UWP). Los identificadores de secuencia estándar asociados a la consola, **stdin,** **stdout**y **stderr**, deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_putchar.c
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

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putchar( *p );
}
```

### <a name="output"></a>Output

```Output
This is the line of output
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
