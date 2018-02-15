---
title: qsort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort
dev_langs:
- C++
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a39f6edf9dfdf2130bfe9d00cc2a9453f48ad9f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="qsort"></a>qsort
Realiza una ordenación rápida. Hay disponible una versión más segura de esta función; vea [qsort_s](../../c-runtime-library/reference/qsort-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `base`  
 Inicio de la matriz de destino.  
  
 `num`  
 Tamaño de la matriz en elementos.  
  
 `width`  
 Tamaño del elemento en bytes.  
  
 `compare`  
 Puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación.  
  
## <a name="remarks"></a>Comentarios  
 La función `qsort` implementa un algoritmo de ordenación rápida para ordenar una matriz de `num` elementos, cada uno de `width` bytes. El argumento `base` es un puntero a la base de la matriz que se va a ordenar. `qsort` sobrescribe esta matriz usando los elementos ordenados.  
  
 `qsort` llama a la rutina `compare` una o varias veces durante la ordenación y pasa los punteros a dos elementos de la matriz en cada llamada.  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 La rutina compara los elementos y devuelve uno de los siguientes valores.  
  
|Valor devuelto por la función de comparación|Descripción|  
|-----------------------------------|-----------------|  
|< 0|`elem1` es menor que `elem2`|  
|0|`elem1` equivalente a `elem2`|  
|> 0|`elem1` es mayor que `elem2`|  
  
 La matriz se clasifica en orden ascendente, de acuerdo con la función de comparación. Para clasificar una matriz en orden decreciente, invierta el sentido de "mayor que" y "menor que" en la función de comparación.  
  
 Esta función valida sus parámetros. Si `compare` o `num` es `NULL`, o si `base` es `NULL` y *`num` es distinto de cero, o bien si `width` es menor que cero, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve la función y `errno` se establece en `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`qsort`|\<stdlib.h> y \<search.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
boy deserves every favor good  
```  
  
## <a name="see-also"></a>Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)