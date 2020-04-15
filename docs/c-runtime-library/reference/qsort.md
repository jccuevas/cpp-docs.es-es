---
title: qsort
ms.date: 4/2/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 09de57e206eb6fd4a75a0a9444332136aeee0e9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338247"
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

*Ancho*<br/>
Tamaño del elemento en bytes.

*Comparar*<br/>
Puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación.

## <a name="remarks"></a>Observaciones

La función **qsort** implementa un algoritmo de ordenación rápida para ordenar una matriz de elementos *numéricos,* cada uno de bytes de *ancho.* La *base* de argumentos es un puntero a la base de la matriz que se va a ordenar. **qsort** sobrescribe esta matriz utilizando los elementos ordenados.

**qsort** llama a la rutina de *comparación* una o más veces durante la ordenación y pasa punteros a dos elementos de matriz en cada llamada.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La rutina compara los elementos y devuelve uno de los siguientes valores.

|Valor devuelto por la función de comparación|Descripción|
|-----------------------------------|-----------------|
|< 0|**elem1** menos que **elem2**|
|0|**elem1** equivalente a **elem2**|
|> 0|**elem1** mayor que **elem2**|

La matriz se clasifica en orden ascendente, de acuerdo con la función de comparación. Para clasificar una matriz en orden decreciente, invierta el sentido de "mayor que" y "menor que" en la función de comparación.

Esta función valida sus parámetros. Si *compare* o *number* es **NULL**, o si *base* es **NULL** y *number* es distinto de cero, o si *width* es menor que cero, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve y **errno** se establece en **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**qsort**|\<stdlib.h> y \<search.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Búsqueda y clasificación](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
