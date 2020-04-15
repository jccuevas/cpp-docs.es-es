---
title: bsearch
ms.date: 4/2/2020
api_name:
- bsearch
- _o_bsearch
api_location:
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: efad391eb2512cfa59cc3597430a84727676f27e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333801"
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

*Clave*\
Puntero a la clave para buscar.

*Base*\
Puntero a la base de los datos de búsqueda.

*Número*\
Número de elementos.

*Ancho*\
Ancho de los elementos.

*Comparar*\
Función de devolución de llamada que compara dos elementos. El primero es un puntero a la clave para la búsqueda y el segundo es un puntero al elemento de matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

**bsearch** devuelve un puntero a una aparición de *clave* en la matriz señalada por *base*. Si no se encuentra la *clave,* la función devuelve **NULL**. Si la matriz no está en orden ascendente o contiene registros duplicados con claves idénticas, el resultado es impredecible.

## <a name="remarks"></a>Observaciones

La función **bsearch** realiza una búsqueda binaria de una matriz ordenada de elementos *numéricos,* cada uno de bytes de *ancho* de tamaño. El valor *base* es un puntero a la base de la matriz que se va a buscar y *key* es el valor que se busca. El parámetro *compare* es un puntero a una rutina proporcionada por el usuario que compara la clave solicitada con un elemento de matriz. Devuelve uno de los siguientes valores que especifican su relación:

|Valor devuelto por *rutina de comparación*|Descripción|
|-----------------------------------------|-----------------|
|\< 0|El valor de clave es menor que el elemento de matriz.|
|0|El valor de clave es igual al elemento de matriz.|
|> 0|El valor de clave es mayor que el elemento de matriz.|

Esta función valida sus parámetros. Si *compare*, *key* o *number* es **NULL**, o si *base* es **NULL** y *number* es distinto de cero, o si *width* es cero, la función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece `EINVAL` en y la función devuelve **NULL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> y \<search.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Búsqueda y clasificación](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
