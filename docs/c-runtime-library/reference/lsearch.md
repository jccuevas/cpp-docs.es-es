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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 73bc82ed57692dee348448d2b523961324203ca9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911332"
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

*número*<br/>
Número de elementos.

*width*<br/>
Ancho de cada elemento de la matriz.

*Compare*<br/>
Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lsearch** devuelve un puntero al elemento de la matriz en la *base* que coincide con la *clave*. Si no se encuentra la clave, **_lsearch** devuelve un puntero al elemento recién agregado al final de la matriz.

## <a name="remarks"></a>Observaciones

La función **_lsearch** realiza una búsqueda lineal de la *clave* Value en una matriz de elementos *Number* , cada uno de los bytes de *ancho* . A diferencia de **bsearch**, **_lsearch** no requiere la ordenación de la matriz. Si no se encuentra la *clave* , **_lsearch** la agrega al final de la matriz e incrementa el *número*.

El argumento *Compare* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación. **_lsearch** llama a la rutina de *comparación* una o más veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. *Compare* debe comparar los elementos y devolver un valor distinto de cero (lo que significa que los elementos son diferentes) o 0 (lo que significa que los elementos son idénticos).

Esta función valida sus parámetros. Si *comparar*, la *clave* o el *número* es **null**, o si la *base* es **null** y el *número* es distinto de cero, o si el *ancho* es menor que cero, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
