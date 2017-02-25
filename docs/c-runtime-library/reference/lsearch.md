---
title: "lsearch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lsearch"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lsearch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lsearch (función)"
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _lsearch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una búsqueda lineal por un valor; agrega al final de la lista si no encontrada.  Una versión más segura de esta función está disponible; vea [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md).  
  
## Sintaxis  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### Parámetros  
 `key`  
 Objeto para buscar.  
  
 `base`  
 Puntero a la base de la matriz que se buscará.  
  
 `num`  
 Número de elementos.  
  
 `width`  
 Ancho de cada elemento de matriz.  
  
 `compare`  
 Puntero a la rutina de comparación.  El primer parámetro es un puntero a la clave de búsqueda.  El segundo parámetro es un puntero a un elemento de matriz que se va a comparar con la clave.  
  
## Valor devuelto  
 Si se encuentra la clave, `_lsearch` devuelve un puntero al elemento de matriz en `base` que coincide con `key`.  Si no se encuentra la clave, `_lsearch` devuelve un puntero al elemento recién agregado al final de la matriz.  
  
## Comentarios  
 La función de `_lsearch` realiza una búsqueda lineal por valor `key` en una matriz de elementos de `num` , cada uno de los bytes de `width` .  A diferencia de `bsearch`, `_lsearch` no requiere una matriz ajustar su tamaño.  Si `key` no se encuentra, `_lsearch` lo agrega al final de la matriz y aumenta `num`.  
  
 El argumento de `compare` es un puntero a una rutina usuario\- proporcionada que compara dos elementos de matriz y devuelve un valor que especifica la relación.  `_lsearch` llama a la rutina de `compare` una o más veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada.  `compare` debe comparar los elementos y devolver cero \(indican los elementos sea diferente\) o 0 \(indican los elementos sea idéntico\).  
  
 Esta función valida sus parámetros.  Si `compare`, `key` o `num` es `NULL`, o si `base` es NULL y \*`num` es distinto de cero, o si `width` es menor que cero, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lsearch`|\<search.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_lsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main(void)  
{  
   char * wordlist[4] = { "hello", "thanks", "bye" };  
                            // leave room to grow...  
   int n = 3;  
   char **result;  
   char *key = "extra";  
   int i;  
  
   printf( "wordlist before _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
  
   result = (char **)_lsearch( &key, wordlist,   
                      &n, sizeof(char *), compare );  
  
   printf( "wordlist after _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
}  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
```  
  
  **lista de palabras antes de \_lsearch: hello goodbye de las gracias**  
**lista de palabras después de \_lsearch: hello extensor de adiós de las gracias**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)