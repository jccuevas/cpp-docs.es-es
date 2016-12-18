---
title: "clearerr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "clearerr"
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
  - "clearerr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "clearerr (función)"
  - "indicador de error para secuencias"
  - "restablecer indicador de error de secuencia"
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# clearerr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Restablece el indicador de error para una secuencia.  Una versión más segura de esta función está disponible; vea [clearerr\_s](../../c-runtime-library/reference/clearerr-s.md).  
  
## Sintaxis  
  
```  
void clearerr(  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Comentarios  
 La función de `clearerr` restablece el indicador de error y la marca de fin de archivo para `stream`.  Los indicadores de error automáticamente no se borran; el indicador de error para una secuencia especificada se establece una vez, las operaciones en esa secuencia seguirán devolviendo un valor de error hasta `clearerr`, `fseek`, `fsetpos`, o se llama `rewind` .  
  
 Si `stream` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, conjuntos `errno` de esta función a `EINVAL` y devolverá.  Para obtener más información sobre `errno` y códigos de error, vea [constantes de errno](../../c-runtime-library/errno-constants.md).  
  
 Una versión más segura de esta función está disponible; vea [clearerr\_s](../../c-runtime-library/reference/clearerr-s.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`clearerr`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_clearerr.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      clearerr( stdin );  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      clearerr( stdin );  
   }  
   else  
      printf( "No read error\n" );  
}  
```  
  
  **`error` de nnWrite: Ningún error**  
**¿La entrada provocará un error? n**  
**Ningún error de lectura**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de errores](../../c-runtime-library/error-handling-crt.md)   
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror, \_wperror](../../c-runtime-library/reference/perror-wperror.md)