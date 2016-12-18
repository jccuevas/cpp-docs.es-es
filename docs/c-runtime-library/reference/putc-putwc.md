---
title: "putc, putwc | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "putwc"
  - "putc"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_puttc"
  - "putwc"
  - "putc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_puttc (función)"
  - "caracteres, escribir"
  - "putc (función)"
  - "puttc (función)"
  - "putwc (función)"
  - "secuencias, escribir caracteres en"
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# putc, putwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un carácter en un flujo.  
  
## Sintaxis  
  
```  
  
      int putc(  
   int c,  
   FILE *stream   
);  
wint_t putwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a escribir.  
  
 `stream`  
 Puntero a la estructura **FILE**.  
  
## Valor devuelto  
 Devuelve el carácter escrito.  Para indicar un error o una condición de final de archivo, `putc` y `putchar` devuelven `EOF`; `putwc` y `putwchar` devuelven **WEOF**.  Para las cuatro rutinas, use [ferror](../../c-runtime-library/reference/ferror.md) o [feof](../../c-runtime-library/reference/feof.md) para comprobar si hay un error o una condición de final de archivo.  Si se pasa un puntero nulo para `stream`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` o **WEOF** y establecen `errno` en `EINVAL`.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 La rutina `putc` escribe el carácter individual `c` en la salida `stream` en la posición actual.  Se puede pasar cualquier entero a `putc`, pero solo se escriben los 8 bits inferiores.  La rutina `putchar` es idéntica a **putc\(** `c`**, stdout \)**.  Para cada rutina, si se produce un error de lectura, se establece el indicador de error para el flujo.  `putc` y `putchar` se parecen a `fputc` y `_fputchar`, respectivamente, pero se implementan como funciones y como macros \(vea [Elegir entre funciones y macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)\).  `putwc` y `putwchar` son versiones con caracteres anchos de `putc` y `putchar`, respectivamente.  `putwc` y `putc` se comportan exactamente igual si el flujo se abre en modo ANSI.  `putc` no admite actualmente la salida en un flujo UNICODE.  
  
 Las versiones con el sufijo de **\_nolock** son idénticas, salvo que no están protegidas contra interferencias de otros subprocesos.  Para obtener más información, vea **\_putc\_nolock, \_putwc\_nolock**.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_puttc`|`putc`|`putc`|**putwc**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`putc`|\<stdio.h\>|  
|`putwc`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
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
  
## Resultados  
  
```  
This is the line of output  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)