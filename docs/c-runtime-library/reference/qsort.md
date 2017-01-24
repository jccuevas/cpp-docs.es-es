---
title: "qsort | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "qsort"
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
  - "qsort"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "qsort (función)"
  - "algoritmo de ordenación rápida"
  - "ordenar matrices"
  - "matrices [CRT], ordenar"
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# qsort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una ordenación rápida.  Una versión más segura de esta función está disponible; vea [qsort\_s](../../c-runtime-library/reference/qsort-s.md).  
  
## Sintaxis  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### Parámetros  
 `base`  
 Inicio de la matriz de destino.  
  
 `num`  
 Tamaño de la matriz de elementos.  
  
 `width`  
 Tamaño del elemento en bytes.  
  
 `compare`  
 Puntero a una rutina usuario\- proporcionada que compara dos elementos de matriz y devuelve un valor que especifica la relación.  
  
## Comentarios  
 La función de `qsort` implementa un algoritmo de la rápido\- ordenación para ordenar una matriz de elementos de `num` , cada uno de los bytes de `width` .  El argumento `base` es un puntero a la base de la matriz que se ordenen.  `qsort` sobrescribe esta matriz mediante los elementos ordenados.  
  
 `qsort` llama a la rutina de `compare` una o más veces durante la ordenación, y pasa punteros a dos elementos de la matriz en cada llamada.  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 La rutina compara los elementos y devuelve uno de los valores siguientes.  
  
|Compare el valor devuelto de la función|Descripción|  
|---------------------------------------------|-----------------|  
|\< 0|`elem1` es menor que `elem2`|  
|0|equivalente de`elem1` a `elem2`|  
|\> 0|`elem1` es mayor que `elem2`|  
  
 La matriz se ordena en sentido petición, definido por la función de comparación.  Para ordenar una matriz en orden descendente, invierta el sentido de “mayor que” y “menor que” en la función de comparación.  
  
 Esta función valida sus parámetros.  Si `compare` o `num` es `NULL`, o si `base` es `NULL` y \*`num` es distinto de cero, o si `width` es menor que cero, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve y `errno` se establece en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`qsort`|\<stdlib.h y\> search.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_qsort.c  
// arguments: every good boy deserves favor  
  
/* This program reads the command-line  
 * parameters and uses qsort to sort them. It  
 * then displays the sorted arguments.  
 */  
  
#include <stdlib.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main( int argc, char **argv )  
{  
   int i;  
   /* Eliminate argv[0] from sort: */  
   argv++;  
   argc--;  
  
   /* Sort remaining args using Quicksort algorithm: */  
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );  
  
   /* Output sorted list: */  
   for( i = 0; i < argc; ++i )  
      printf( " %s", argv[i] );  
   printf( "\n" );  
}  
  
int compare( const void *arg1, const void *arg2 )  
{  
   /* Compare all of both strings: */  
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );  
}  
```  
  
  **el chico merece cada favor kind**   
## Equivalente en .NET Framework  
 [System::Collections::ArrayList::Sort](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)