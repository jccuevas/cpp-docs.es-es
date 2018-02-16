---
title: _lfind | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _lfind
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lfind
- _lfind
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b6df994306ad9a7d51d619a9bd409c021386a11
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="lfind"></a>_lfind
Realiza una búsqueda lineal de la clave especificada. Existe una versión más segura disponible de esta función; vea [_lfind_s](../../c-runtime-library/reference/lfind-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `key`  
 Objeto que se va a buscar.  
  
 `base`  
 Puntero a la base de los datos de búsqueda.  
  
 `num`  
 Número de elementos de la matriz.  
  
 `width`  
 Ancho de los elementos de la matriz.  
  
 `compare`  
 Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero al elemento de la matriz que se va a comparar con la clave.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se encuentra la clave, `_lfind` devuelve un puntero al elemento de la matriz en `base` que coincide con `key`. Si no se encuentra la clave, `_lfind` devuelve `NULL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_lfind` realiza una búsqueda lineal del valor `key` en una matriz de `num` elementos, cada uno de ellos de `width` bytes. A diferencia de `bsearch`, para `_lfind` no es necesario que la matriz esté ordenada. El argumento `base` es un puntero a la base de la matriz que se va a buscar. El argumento `compare` es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y luego devuelve un valor que especifica su relación. `_lfind` llama a la rutina `compare` una o varias veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. La rutina `compare` debe comparar los elementos y luego devolver un valor distinto de cero (es decir, los elementos son diferentes) o 0 (es decir, los elementos son idénticos).  
  
 Esta función valida sus parámetros. Si `compare`, `key` o `num` es `NULL`, o si `base` es NULL y *`num` es distinto de cero, o si `width` es menor que cero, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_lfind`|\<search.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
Hello found  
```  
  
## <a name="see-also"></a>Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)