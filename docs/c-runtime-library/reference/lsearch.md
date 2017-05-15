---
title: _lsearch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lsearch
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
- _lsearch
- lsearch
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 86dd9925775d50a8e1c79f677f3e5b1d9ad3ae37
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="lsearch"></a>_lsearch
Realiza una búsqueda lineal de un valor; lo agrega al final de la lista si no se encuentra. Existe una versión más segura disponible de esta función; vea [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `key`  
 Objeto que se va a buscar.  
  
 `base`  
 Puntero a la base de la matriz en la que se va a buscar.  
  
 `num`  
 Número de elementos.  
  
 `width`  
 Ancho de cada elemento de la matriz.  
  
 `compare`  
 Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se encuentra la clave, `_lsearch` devuelve un puntero al elemento de la matriz en `base` que coincide con `key`. Si no se encuentra la clave, `_lsearch` devuelve un puntero al elemento recién agregado al final de la matriz.  
  
## <a name="remarks"></a>Comentarios  
 La función `_lsearch` realiza una búsqueda lineal del valor `key` en una matriz de `num` elementos, cada uno de ellos de `width` bytes. A diferencia de `bsearch`, para `_lsearch` no es necesario que la matriz esté ordenada. Si no se encuentra `key`, `_lsearch` lo agrega al final de la matriz e incrementa `num`.  
  
 El argumento `compare` es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y luego devuelve un valor que especifica su relación. `_lsearch` llama a la rutina `compare` una o varias veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. `compare` debe comparar los elementos y luego devolver un valor distinto de cero (es decir, los elementos son diferentes) o 0 (es decir, los elementos son idénticos).  
  
 Esta función valida sus parámetros. Si `compare`, `key` o `num` es `NULL`, o si `base` es NULL y *`num` es distinto de cero, o si `width` es menor que cero, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_lsearch`|\<search.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
wordlist before _lsearch: hello thanks bye  
wordlist after _lsearch: hello thanks bye extra  
```  
  
## <a name="see-also"></a>Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)
