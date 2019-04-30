---
title: qsort
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 8a770965a03e43227b99f122924c723691f79c61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358104"
---
# <a name="qsort"></a>qsort

Realiza una ordenación rápida. Hay disponible una versión más segura de esta función; vea [qsort_s](qsort-s.md).

## <a name="syntax"></a>Sintaxis

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Parámetros

*base*<br/>
Inicio de la matriz de destino.

*number*<br/>
Tamaño de la matriz en elementos.

*width*<br/>
Tamaño del elemento en bytes.

*compare*<br/>
Puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación.

## <a name="remarks"></a>Comentarios

El **qsort** función implementa un algoritmo de ordenación rápida para ordenar una matriz de *número* elementos, cada uno de *ancho* bytes. El argumento *base* es un puntero a la base de la matriz esté ordenada. **qsort** sobrescribe esta matriz mediante el uso de los elementos ordenados.

**qsort** llamadas la *comparar* rutinaria uno o más veces durante la ordenación y pasa los punteros a dos elementos de matriz en cada llamada.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La rutina compara los elementos y devuelve uno de los siguientes valores.

|Valor devuelto por la función de comparación|Descripción|
|-----------------------------------|-----------------|
|< 0|**elem1** menor **elem2**|
|0|**elem1** equivalente a **elem2**|
|> 0|**elem1** mayor **elem2**|

La matriz se clasifica en orden ascendente, de acuerdo con la función de comparación. Para clasificar una matriz en orden decreciente, invierta el sentido de "mayor que" y "menor que" en la función de comparación.

Esta función valida sus parámetros. Si *comparar* o *número* es **NULL**, o si *base* es **NULL** y *número* es distinto de cero, o si *ancho* es menor que cero, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve y **errno** está establecido en **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**qsort**|\<stdlib.h> y \<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
