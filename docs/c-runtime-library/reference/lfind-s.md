---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
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
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 8f2983bee93c623eb936ed12422134281418076b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342185"
---
# <a name="_lfind_s"></a>_lfind_s

Realiza una búsqueda lineal de la clave especificada. Versión de [_lfind](lfind.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de los datos de búsqueda.

*number*<br/>
Número de elementos de la matriz.

*Tamaño*<br/>
Tamaño de los elementos de la matriz expresados en bytes.

*Comparar*<br/>
Puntero a la rutina de comparación. El primer parámetro es el puntero de *contexto.* El segundo parámetro es un puntero a la clave de búsqueda. El tercer parámetro es un puntero al elemento de la matriz que se va a comparar con la clave.

*contextoo*<br/>
Un puntero a un objeto al que se podría obtener acceso en la función de comparación.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lfind_s** devuelve un puntero al elemento de la matriz en *la base* que coincide con la *clave*. Si no se encuentra la clave, **_lfind_s** devuelve **NULL**.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, como se describe en validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y la función devuelve **NULL**.

### <a name="error-conditions"></a>Condiciones de error

|key|base|compare|num|tamaño|errno|
|---------|----------|-------------|---------|----------|-----------|
|**Null**|cualquiera|cualquiera|cualquiera|cualquiera|**EINVAL**|
|cualquiera|**Null**|cualquiera|!= 0|cualquiera|**EINVAL**|
|cualquiera|cualquiera|cualquiera|cualquiera|cero|**EINVAL**|
|cualquiera|cualquiera|**Null**|an|cualquiera|**EINVAL**|

## <a name="remarks"></a>Observaciones

La función **_lfind_s** realiza una búsqueda lineal de la *clave* de valor en una matriz de elementos *numéricos,* cada uno de bytes de *ancho.* A diferencia de **bsearch_s**, **_lfind_s** no requiere que se ordene la matriz. El argumento *base* es un puntero a la base de la matriz que se va a buscar. El argumento *compare* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de matriz y, a continuación, devuelve un valor que especifica su relación. **_lfind_s** llama a la rutina de *comparación* una o más veces durante la búsqueda, pasando el puntero de *contexto* y punteros a dos elementos de matriz en cada llamada. La rutina *de comparación* debe comparar los elementos y, a continuación, devolver distinto de cero (lo que significa que los elementos son diferentes) o 0 (lo que significa que los elementos son idénticos).

**_lfind_s** es similar a **_lfind** excepto por la adición del puntero de *contexto* a los argumentos de la función de comparación y la lista de parámetros de la función. El puntero de *contexto* puede ser útil si la estructura de datos buscada forma parte de un objeto y la función *de comparación* necesita tener acceso a los miembros del objeto. La función *compare* puede convertir el puntero void en el tipo de objeto adecuado y tener acceso a los miembros de ese objeto. La adición del parámetro *context* hace **que _lfind_s** sea más seguro porque se puede usar contexto adicional para evitar errores de reentrada asociados con el uso de variables estáticas para que los datos estén disponibles para la función *de comparación.*

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_lfind_s.cpp
// This program uses _lfind_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char *s1 = *(char**)str1;
    char *s2 = *(char**)str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

void find_it( char *key, char *array[], unsigned int num, locale &loc )
{
   char **result = (char **)_lfind_s( &key, array,
                      &num, sizeof(char *), compare, &loc );
   if( result )
      printf( "%s found\n", *result );
   else
      printf( "%s not found\n", key );
}

int main( )
{
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );
}
```

```Output
weit found
```

## <a name="see-also"></a>Consulte también

[Búsqueda y clasificación](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
