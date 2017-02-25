---
title: "fputc, fputwc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fputc"
  - "fputwc"
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
  - "fputc"
  - "fputwc"
  - "_fputtc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fputtc (función)"
  - "fputc (función)"
  - "fputtc (función)"
  - "fputwc (función)"
  - "secuencias, escribir caracteres en"
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# fputc, fputwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un carácter en un flujo.  
  
## Sintaxis  
  
```  
int fputc(  
   int c,  
   FILE *stream   
);  
wint_t fputwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a escribir.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el carácter escrito.  En el caso de `fputc`, el valor `EOF` devuelto indica un error.  En el caso de `fputwc`, el valor `WEOF` devuelto indica un error.  Si `stream` es `NULL`, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 Cada una de estas funciones escribe el carácter único `c` en un archivo, en la posición indicada por el indicador de posición de archivo asociado \(si está definido\) y hace avanzar el indicador según corresponda.  En el caso de `fputc` y `fputwc`, el archivo se asocia a `stream`*.* Si el archivo no admite solicitudes de posición o no se abrió en modo Append, el carácter se anexa al final del flujo.  
  
 Las dos funciones se comportan igual si el flujo se abre en modo ANSI.  `fputc` no admite actualmente la salida a un flujo UNICODE.  
  
 Las versiones con el sufijo `_nolock` son idénticas, salvo que no están protegidas contra interferencias de otros subprocesos.  Para obtener más información, vea[\_fputc\_nolock, \_fputwc\_nolock](../../c-runtime-library/reference/fputc-nolock-fputwc-nolock.md).  
  
 Comentarios específicos de la rutina.  
  
|Rutina|Comentarios|  
|------------|-----------------|  
|`fputc`|Equivale a `putc`, pero implementado solo como función, y no como una función y una macro.|  
|`fputwc`|Versión de caracteres anchos de `fputc`.  Escribe `c` como carácter multibyte o carácter ancho en función de que `stream` se haya abierto en modo de texto o modo binario.|  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_fputtc`|`fputc`|`fputc`|`fputwc`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fputc`|\<stdio.h\>|  
|`fputwc`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_fputc.c  
// This program uses fputc  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of fputc!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
  **This is a test of fputc\!\!**   
## Equivalente en .NET Framework  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)