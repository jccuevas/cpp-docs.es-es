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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3d9c3481b37e94dbb59ee7356caafc53501045ea
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913259"
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

*número*<br/>
Tamaño de la matriz en elementos.

*width*<br/>
Tamaño del elemento en bytes.

*Compare*<br/>
Puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación.

## <a name="remarks"></a>Observaciones

La función **qsort** implementa un algoritmo de ordenación rápida para ordenar una matriz de elementos *numéricos* , cada uno de los bytes de *ancho* . La *base* del argumento es un puntero a la base de la matriz que se va a ordenar. **qsort** sobrescribe esta matriz mediante los elementos ordenados.

**qsort** llama a la rutina de *comparación* una o más veces durante la ordenación y pasa los punteros a dos elementos de la matriz en cada llamada.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La rutina compara los elementos y devuelve uno de los siguientes valores.

|Valor devuelto por la función de comparación|Descripción|
|-----------------------------------|-----------------|
|< 0|**Elem1** menor que **Elem2**|
|0|**Elem1** equivalente a **Elem2**|
|> 0|**Elem1** mayor que **Elem2**|

La matriz se clasifica en orden ascendente, de acuerdo con la función de comparación. Para clasificar una matriz en orden decreciente, invierta el sentido de "mayor que" y "menor que" en la función de comparación.

Esta función valida sus parámetros. Si *comparar* o *número* es **null**, o si la *base* es **null** y el *número* es distinto de cero, o si el *ancho* es menor que cero, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve y **errno** se establece en **EINVAL**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
