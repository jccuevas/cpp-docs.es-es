---
title: _lfind
ms.date: 11/04/2016
api_name:
- _lfind
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: ec59340433b92334effa8004720e4f0756085670
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442921"
---
# <a name="_lfind"></a>_lfind

Realiza una búsqueda lineal de la clave especificada. Existe una versión más segura disponible de esta función; vea [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de los datos de búsqueda.

*número*<br/>
Número de elementos de la matriz.

*width*<br/>
Ancho de los elementos de la matriz.

*compare*<br/>
Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero al elemento de la matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lfind** devuelve un puntero al elemento de la matriz en la *base* que coincide con la *clave*. Si no se encuentra la clave, **_lfind** devuelve **null**.

## <a name="remarks"></a>Observaciones

La función **_lfind** realiza una búsqueda lineal de la *clave* Value en una matriz de elementos *Number* , cada uno de los bytes de *ancho* . A diferencia de **bsearch**, **_lfind** no requiere la ordenación de la matriz. El argumento *base* es un puntero a la base de la matriz que se va a buscar. El argumento *Compare* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y, a continuación, devuelve un valor que especifica su relación. **_lfind** llama a la rutina de *comparación* una o más veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. La rutina de *comparación* debe comparar los elementos y devolver un valor distinto de cero (es decir, los elementos son diferentes) o 0 (lo que significa que los elementos son idénticos).

Esta función valida sus parámetros. Si *comparar*, la *clave* o el *número* es **null**, o si la *base* es **null** y el *número* es distinto de cero, o si el *ancho* es menor que cero, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

## <a name="see-also"></a>Consulte también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
