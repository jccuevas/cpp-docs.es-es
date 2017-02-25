---
title: "lfind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lfind"
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
  - "lfind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lfind (función)"
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _lfind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una búsqueda lineal para la clave especificada.  Una versión más segura de esta función está disponible; vea [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md).  
  
## Sintaxis  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### Parámetros  
 `key`  
 Objeto para buscar.  
  
 `base`  
 Puntero a la base de datos de búsqueda.  
  
 `num`  
 Número de elementos de la matriz.  
  
 `width`  
 Ancho de los elementos de matriz.  
  
 `compare`  
 Puntero a la rutina de comparación.  El primer parámetro es un puntero a cerrar para la búsqueda.  El segundo parámetro es un puntero al elemento de matriz que se va a comparar con la clave.  
  
## Valor devuelto  
 Si se encuentra la clave, `_lfind` devuelve un puntero al elemento de matriz en `base` que coincide con `key`.  Si no se encuentra la clave, `_lfind` devuelve `NULL`.  
  
## Comentarios  
 La función de `_lfind` realiza una búsqueda lineal por valor `key` en una matriz de elementos de `num` , cada uno de los bytes de `width` .  A diferencia de `bsearch`, `_lfind` no requiere una matriz ajustar su tamaño.  El argumento de `base` es un puntero a la base de la matriz que se buscará.  El argumento de `compare` es un puntero a una rutina usuario\- proporcionada que compara dos elementos de matriz y después devuelve un valor que especifica la relación.  `_lfind` llama a la rutina de `compare` una o más veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada.  La rutina de `compare` debe comparar los elementos y después devolver cero \(indican los elementos sea diferente\) o 0 \(indican los elementos sea idéntico\).  
  
 Esta función valida sus parámetros.  Si `compare`, `key` o `num` es `NULL`, o si `base` es NULL y \*`num` es distinto de cero, o si `width` es menor que cero, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lfind`|\<search.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_lfind.c  
// This program uses _lfind to search a string array  
// for an occurrence of "hello".  
  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
  
int main( )  
{  
   char *arr[] = {"Hi", "Hello", "Bye"};  
   int n = sizeof(arr) / sizeof(char*);  
   char **result;  
   char *key = "hello";  
  
   result = (char **)_lfind( &key, arr,   
                      &n, sizeof(char *), compare );  
  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "hello not found!\n" );  
}  
```  
  
  **Hello encontrado**   
## Equivalente en .NET Framework  
 [System::Collections::ArrayList::Contains](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)