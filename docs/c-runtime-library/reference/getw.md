---
title: "_getw | Microsoft Docs"
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
  - "_getw"
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
  - "_getw"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getw (función)"
  - "getw (función)"
  - "enteros, obtener de secuencias"
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getw
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un entero de una secuencia.  
  
## Sintaxis  
  
```  
int _getw(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## Valor devuelto  
 `_getw` devuelve la lectura del valor entero.  Un valor devuelto de `EOF` indica un error o el final del archivo.  Sin embargo, como el valor de `EOF` también es un valor entero, un uso `feof` o `ferror` legítimo para comprobar un final de archivo o una condición de error.  Si `stream` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EOF`.  
  
## Comentarios  
 La función de `_getw` lee el valor binario siguiente de `int` tipo de archivo asociado a `stream` y aumenta el puntero de archivo asociado \(si hay alguno\) para señalar al carácter no leídos siguiente.  `_getw` no supone ninguna alineación especial de elementos de la secuencia.  Los problemas con trasladar pueden aparecer con `_getw` porque el tamaño de `int` escrito y el orden de bytes dentro del tipo de `int` difieren entre los sistemas.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getw`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_getw.c  
// This program uses _getw to read a word  
// from a stream, then performs an error check.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   int i;  
  
   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )  
      printf( "Couldn't open file\n" );  
   else  
   {  
      // Read a word from the stream:  
      i = _getw( stream );  
  
      // If there is an error...  
      if( ferror( stream ) )  
      {  
         printf( "_getw failed\n" );  
         clearerr_s( stream );  
      }  
      else  
         printf( "First data word in file: 0x%.4x\n", i );  
      fclose( stream );  
   }  
}  
```  
  
## Entrada: crt\_getw.txt  
  
```  
Line one.  
Line two.  
```  
  
### Resultados  
  
```  
First data word in file: 0x656e694c  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_putw](../../c-runtime-library/reference/putw.md)