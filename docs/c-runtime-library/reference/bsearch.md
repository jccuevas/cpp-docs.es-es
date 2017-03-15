---
title: "bsearch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "bsearch"
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
  - "bsearch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [CRT], búsqueda binaria"
  - "bsearch (función)"
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# bsearch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una búsqueda binaria de una matriz ordenada. Existe una versión más segura disponible de esta función; vea [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md).  
  
## Sintaxis  
  
```  
void *bsearch(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) (const void *key, const void *datum)   
);  
```  
  
#### Parámetros  
 `key`  
 Objeto que se va a buscar.  
  
 `base`  
 Puntero a la base de datos de búsqueda.  
  
 `num`  
 Número de elementos.  
  
 `width`  
 Ancho de los elementos.  
  
 `compare`  
 Función de devolución de llamada que compara dos elementos. El primero es un puntero a la clave de la búsqueda y el segundo es un puntero al elemento de matriz que se va a comparar con la clave.  
  
## Valor devuelto  
 `bsearch` devuelve un puntero a una instancia de `key` de la matriz que `base` señala. Si no encuentra `key`, la función devuelve `NULL`. Si la matriz no está en orden ascendente o contiene registros duplicados con claves idénticas, el resultado es impredecible.  
  
## Comentarios  
 La función `bsearch` realiza una búsqueda binaria de una matriz ordenada de elementos `num`, cada uno de ellos de `width` bytes de tamaño. El valor `base` es un puntero a la base de la matriz que se va a buscar y `key` es el valor buscado. El parámetro `compare` es un puntero a una rutina proporcionada por el usuario que compara la clave solicitada con un elemento de matriz y devuelve uno de los siguientes valores que especifica su relación:  
  
|Valor devuelto por la rutina `compare`|Descripción|  
|--------------------------------------------|-----------------|  
|\< 0|El valor de clave es menor que el elemento de matriz.|  
|0|El valor de clave es igual al elemento de matriz.|  
|\> 0|La clave es mayor que el elemento de matriz.|  
  
 Esta función valida sus parámetros. Si `compare`, `key` o `num` es `NULL`, o si `base` es `NULL` y \*`num` es distinto de cero, o si `width` es cero, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`bsearch`|\<stdlib.h\> y \<search.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este programa ordena una matriz de cadenas con qsort y, luego, usa bsearch para buscar la palabra "cat".  
  
```  
// crt_bsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( char **arg1, char **arg2 )  
{  
   /* Compare all of both strings: */  
   return _strcmpi( *arg1, *arg2 );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
   char **result;  
   char *key = "cat";  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const   
   void*, const void*))compare );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),  
                              sizeof( char * ), (int (*)(const void*, const void*))compare );  
   if( result )  
      printf( "\n%s found at %Fp\n", *result, result );  
   else  
      printf( "\nCat not found!\n" );  
}  
```  
  
```Output  
cat cow dog goat horse human pig rat cat found at 002F0F04  
```  
  
## Equivalente en .NET Framework  
 [System::Collections::ArrayList::BinarySearch](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.binarysearch.aspx)  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)