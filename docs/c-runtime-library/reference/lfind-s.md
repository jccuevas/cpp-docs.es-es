---
title: _lfind_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lfind_s
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
- lfind_s
- _lfind_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 963b657a009f7376a17706b4ac1e5fb4e8b69237
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="lfinds"></a>_lfind_s

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

*Número*<br/>
Número de elementos de la matriz.

*size*<br/>
Tamaño de los elementos de la matriz expresados en bytes.

*compare*<br/>
Puntero a la rutina de comparación. El primer parámetro es el *contexto* puntero. El segundo parámetro es un puntero a la clave de búsqueda. El tercer parámetro es un puntero al elemento de la matriz que se va a comparar con la clave.

*Contexto*<br/>
Un puntero a un objeto al que se podría obtener acceso en la función de comparación.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lfind_s** devuelve un puntero al elemento de la matriz en *base* que coincida con *clave*. Si no se encuentra la clave, **_lfind_s** devuelve **NULL**.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**.

### <a name="error-conditions"></a>Condiciones de error

|key|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|cero|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Comentarios

El **_lfind_s** función realiza una búsqueda lineal para el valor *clave* en una matriz de *número* elementos, cada uno de los *ancho* bytes. A diferencia de **bsearch_s**, **_lfind_s** no requiere que la matriz se ordenen. El *base* argumento es un puntero a la base de la matriz que se debe buscar. El *comparar* argumento es un puntero a una rutina proporcionada por el usuario que compara dos elementos de matriz y, a continuación, devuelve un valor que especifica la relación. **_lfind_s** llamadas el *comparar* rutinas una o varias veces durante la búsqueda, pasando el *contexto* puntero y punteros a dos elementos de la matriz en cada llamada. El *comparar* rutina debe comparar los elementos, a continuación, devolver es distinto de cero (lo que significa que los elementos son diferentes) o 0 (es decir, los elementos son idénticos).

**_lfind_s** es similar a **_lfind** excepto por la adición de la *contexto* puntero a los argumentos de la función de comparación y la lista de parámetros de la función. El *contexto* puntero puede ser útil si la estructura de datos de búsqueda es parte de un objeto y el *comparar* función necesita tener acceso a los miembros del objeto. El *comparar* función puede convertir el puntero void en los miembros de tipo y el acceso de objeto correspondiente de ese objeto. La adición de la *contexto* parámetro hace **_lfind_s** más segura, porque puede usarse contexto adicional para evitar errores de reentrada asociados con el uso de variables estáticas para disponer de datos para el *comparar* función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
