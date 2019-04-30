---
title: _lsearch
ms.date: 11/04/2016
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
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 340e8ac382972b15acc52013d5d6a51352db969c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285661"
---
# <a name="lsearch"></a>_lsearch

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

*width*<br/>
Ancho de cada elemento de la matriz.

*compare*<br/>
Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lsearch** devuelve un puntero al elemento de la matriz en *base* que coincida con *clave*. Si no se encuentra la clave, **_lsearch** devuelve un puntero al elemento recién agregado al final de la matriz.

## <a name="remarks"></a>Comentarios

El **_lsearch** función realiza una búsqueda lineal del valor *clave* en una matriz de *número* elementos, cada uno de *ancho* bytes. A diferencia de **bsearch**, **_lsearch** no requiere la matriz esté ordenada. Si *clave* no se encuentra, **_lsearch** lo agrega al final de la matriz e incrementa *número*.

El *comparar* argumento es un puntero a una rutina proporcionada por el usuario que compara dos elementos de matriz y devuelve un valor que especifica su relación. **_lsearch** llamadas la *comparar* rutinarias una o varias veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. *comparar* debe comparar los elementos y devolver uno distinto de cero (es decir, los elementos son diferentes) o 0 (es decir, los elementos son idénticos).

Esta función valida sus parámetros. Si *comparar*, *clave* o *número* es **NULL**, o si *base* es **NULL**y *número* es distinto de cero, o si *ancho* es menor que cero, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
