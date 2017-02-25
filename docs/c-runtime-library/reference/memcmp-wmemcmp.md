---
title: "memcmp, wmemcmp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "memcmp"
  - "wmemcmp"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "memcmp"
  - "wmemcmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memcmp (función)"
  - "wmemcmp (función)"
ms.assetid: 0c21c3e3-8ee4-40e5-add1-eb26d225fd8d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# memcmp, wmemcmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara los caracteres de dos búferes.  
  
## Sintaxis  
  
```  
  
      int memcmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count  
);  
int wmemcmp(  
   const wchar_t * buf1,  
   const wchar_t * buf2,  
   size_t count  
);  
```  
  
#### Parámetros  
 `buf1`  
 Primer búfer.  
  
 `buf2`  
 Segundo búfer.  
  
 `count`  
 Número de caracteres que se van a comparar. \(Compara los bytes de `memcmp` y los caracteres anchos de `wmemcmp`\).  
  
## Valor devuelto  
 El valor devuelto indica la relación entre los búferes.  
  
|Valor devuelto|Relación de los primeros caracteres `count` de buf1 y buf2|  
|--------------------|----------------------------------------------------------------|  
|\< 0|`buf1` es menor que `buf2`|  
|0|`buf1` es idéntica a `buf2`|  
|\> 0|`buf1` es mayor que `buf2`|  
  
## Comentarios  
 Compara los primeros caracteres `count` de `buf1` y `buf2` y devuelve un valor que indica la relación entre ellos.  El signo de un valor devuelto distinto de cero es el signo de la diferencia entre el primer par de valores de los búferes.  Los valores se interpretan como `unsigned char` para `memcmp` y como `wchar_t` para `wmemcmp`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`memcmp`|\<memory.h\> o \<string.h\>|  
|`wmemcmp`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de la [biblioteca en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_memcmp.c  
/* This program uses memcmp to compare  
 * the strings named first and second. If the first  
 * 19 bytes of the strings are equal, the program  
 * considers the strings to be equal.  
 */  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char first[]  = "12345678901234567890";  
   char second[] = "12345678901234567891";  
   int int_arr1[] = {1,2,3,4};  
   int int_arr2[] = {1,2,3,4};  
   int result;  
  
   printf( "Compare '%.19s' to '%.19s':\n", first, second );  
   result = memcmp( first, second, 19 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else  
      printf( "First is greater than second.\n" );  
  
   printf( "Compare '%d,%d' to '%d,%d':\n", int_arr1[0], int_arr1[1], int_arr2[0], int_arr2[1]);  
   result = memcmp( int_arr1, int_arr2, sizeof(int) * 2 );  
   if( result < 0 )  
      printf( "int_arr1 is less than int_arr2.\n" );  
   else if( result == 0 )  
      printf( "int_arr1 is equal to int_arr2.\n" );  
   else   
      printf( "int_arr1 is greater than int_arr2.\n" );  
}  
```  
  
## Resultados  
  
```  
Compare '1234567890123456789' to '1234567890123456789':  
First is equal to second.  
Compare '1,2' to '1,2':  
int_arr1 is equal to int_arr2.  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)