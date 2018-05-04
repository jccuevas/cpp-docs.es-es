---
title: bsearch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- bsearch
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
- bsearch
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77d7576b5e8914148a8c67d8df82573c1f379e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="bsearch"></a>bsearch

Realiza una búsqueda binaria de una matriz ordenada. Hay disponible una versión más segura de esta función; consulte [bsearch_s](bsearch-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de datos de búsqueda.

*Número*<br/>
Número de elementos.

*width*<br/>
Ancho de los elementos.

*compare*<br/>
Función de devolución de llamada que compara dos elementos. El primero es un puntero a la clave de la búsqueda y el segundo es un puntero al elemento de matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

**bsearch** devuelve un puntero a una instancia de *clave* en la matriz señalada por *base*. Si *clave* no se encuentra, la función devuelve **NULL**. Si la matriz no está en orden ascendente o contiene registros duplicados con claves idénticas, el resultado es impredecible.

## <a name="remarks"></a>Comentarios

El **bsearch** función realiza una búsqueda binaria de una matriz ordenada de *número* elementos, cada uno de los *ancho* el tamaño en bytes. El *base* value es un puntero a la base de la matriz que desea buscar, y *clave* es el valor que se van a buscar. El *comparar* parámetro es un puntero a una rutina proporcionada por el usuario que compara la clave solicitada en un elemento de matriz y devuelve uno de los siguientes valores que especifica su relación:

|Valor devuelto por *comparar* rutina|Descripción|
|-----------------------------------------|-----------------|
|\< 0|El valor de clave es menor que el elemento de matriz.|
|0|El valor de clave es igual al elemento de matriz.|
|> 0|La clave es mayor que el elemento de matriz.|

Esta función valida sus parámetros. Si *comparar*, *clave* o *número* es **NULL**, o si *base* es **NULL**y **número* es distinto de cero, o si *ancho* es cero, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> y \<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa ordena una matriz de cadenas con qsort y, luego, usa bsearch para buscar la palabra "cat".

```C
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
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>Vea también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
