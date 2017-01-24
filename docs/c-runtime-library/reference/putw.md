---
title: "_putw | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putw"
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
  - "_putw"
  - "putw"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putw (función)"
  - "enteros, escribir en secuencias"
  - "putw (función)"
  - "secuencias, escribir enteros en"
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putw
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escriba un entero a una secuencia.  
  
## Sintaxis  
  
```  
  
      int _putw(  
   int binint,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 *binint*  
 Entero binario que se generará.  
  
 `stream`  
 Puntero a la estructura de **FILE**.  
  
## Valor devuelto  
 Devuelve el valor con tipo.  Un valor devuelto de `EOF` podría indicar un error.  Dado que `EOF` también es un valor entero legítimo, utilice `ferror` de comprobar un error.  Si `stream` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EOF`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_putw` escribe un valor binario de `int` escritos en la posición actual *de la secuencia.* `_putw` no afecta a la alineación de elementos de la secuencia ni se supone ninguna alineación especial.  `_putw` sirve principalmente para la compatibilidad con bibliotecas anteriores.  Problemas de portabilidad pueden producirse con `_putw` porque el tamaño de `int` y el orden de bytes dentro de `int` difieren entre los sistemas.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_putw`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_putw.c  
/* This program uses _putw to write a  
 * word to a stream, then performs an error check.  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   unsigned u;  
   if( fopen_s( &stream, "data.out", "wb" ) )  
      exit( 1 );  
   for( u = 0; u < 10; u++ )  
   {  
      _putw( u + 0x2132, stream );   /* Write word to stream. */  
      if( ferror( stream ) )         /* Make error check. */  
      {  
         printf( "_putw failed" );  
         clearerr_s( stream );  
         exit( 1 );  
      }  
   }  
   printf( "Wrote ten words\n" );  
   fclose( stream );  
}  
```  
  
## Resultados  
  
```  
Wrote ten words  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_getw](../../c-runtime-library/reference/getw.md)