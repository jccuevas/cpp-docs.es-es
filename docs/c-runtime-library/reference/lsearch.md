---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: a6ef3d86ffe8f03da34d4a374bddda1452815672
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341643"
---
# <a name="_lsearch"></a>_lsearch

Realiza una búsqueda lineal de un valor; lo agrega al final de la lista si no se encuentra. Existe una versión más segura disponible de esta función; vea [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de la matriz en la que se va a buscar.

*number*<br/>
Número de elementos.

*Ancho*<br/>
Ancho de cada elemento de la matriz.

*Comparar*<br/>
Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lsearch** devuelve un puntero al elemento de la matriz en *la base* que coincide con la *clave*. Si no se encuentra la clave, **_lsearch** devuelve un puntero al elemento recién agregado al final de la matriz.

## <a name="remarks"></a>Observaciones

La función **_lsearch** realiza una búsqueda lineal de la *clave* de valor en una matriz de elementos *numéricos,* cada uno de bytes de *ancho.* A diferencia de **bsearch**, **_lsearch** no requiere que se ordene la matriz. Si no se encuentra la *clave,* **_lsearch** la agrega al final de la matriz e incrementa el *número*.

El argumento *compare* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de matriz y devuelve un valor que especifica su relación. **_lsearch** llama a la rutina de *comparación* una o más veces durante la búsqueda, pasando punteros a dos elementos de matriz en cada llamada. *comparar* debe comparar los elementos y devolver distinto de cero (lo que significa que los elementos son diferentes) o 0 (lo que significa que los elementos son idénticos).

Esta función valida sus parámetros. Si *compare*, *key* o *number* es **NULL**, o si *base* es **NULL** y *number* es distinto de cero, o si *width* es menor que cero, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y la función devuelve **NULL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

## <a name="see-also"></a>Consulte también

[Búsqueda y clasificación](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
