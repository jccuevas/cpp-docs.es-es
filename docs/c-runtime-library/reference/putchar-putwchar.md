---
title: putchar, putwchar | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- putchar
- putwchar
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
- putchar
- putwchar
- _puttchar
dev_langs:
- C++
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 687cacfbf59f2d905de8f14bcebb6e7bbf68fb53
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="putchar-putwchar"></a>putchar, putwchar
Escribe un carácter en **stdout**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int putchar(  
   int c   
);  
wint_t putwchar(  
   wchar_t c   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que se va a escribir.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el carácter escrito. Para indicar un error o una condición de final de archivo, `putc` y `putchar` devuelven `EOF`, mientras que `putwc` y `putwchar` devuelven **WEOF**. Para las cuatro rutinas, use [ferror](../../c-runtime-library/reference/ferror.md) o [feof](../../c-runtime-library/reference/feof.md) para comprobar si hay un error o una condición de final de archivo. Si se pasa un puntero nulo para `stream`, estas funciones generan una excepción de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven `EOF` o **WEOF** y establecen `errno` en `EINVAL`.  
  
 Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## <a name="remarks"></a>Comentarios  
 La rutina `putc` escribe el carácter individual `c` en la salida `stream` en la posición actual. Se puede pasar cualquier entero a `putc`, pero solo se escriben los 8 bits inferiores. La rutina `putchar` es idéntica a **putc(** `c`**, stdout)**. Para cada rutina, si se produce un error de lectura, se establece el indicador de error para el flujo. `putc` y `putchar` se parecen a `fputc` y `_fputchar`, respectivamente, pero se implementan como funciones y como macros (vea [Elegir entre funciones y macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). `putwc` y `putwchar` son versiones con caracteres anchos de `putc` y `putchar`, respectivamente.  
  
 Las versiones que tienen el sufijo **_nolock** son idénticas, salvo que no están protegidas contra las interferencias de otros subprocesos. Pueden ser más rápidas, porque no incurren en la sobrecarga de bloquear otros subprocesos. Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_puttchar`|`putchar`|`putchar`|**putwchar**|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`putchar`|\<stdio.h>|  
|`putwchar`|\<stdio.h> o \<wchar.h>|  
  
La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, `stdin`, `stdout`, y `stderr`, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
## <a name="output"></a>Salida  
  
```  
This is the line of output  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)