---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: 91b015eb9005a9b447cdd9d74a38d7169bd90a73
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913388"
---
# <a name="bsearch_s"></a>bsearch_s

Realiza una búsqueda binaria de una matriz ordenada. Esta función es una versión de [bsearch](bsearch.md) con mejoras de seguridad, tal y como se describe en [características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>Parámetros

*clave*\
Puntero a la clave que se va a buscar.

*básica*\
Puntero a la base de los datos de búsqueda.

*number*\
Número de elementos.

*Ancho*\
Ancho de los elementos.

*Compare*\
Función de devolución de llamada que compara dos elementos. El primer argumento es el puntero de *contexto* . El segundo argumento es un puntero a la *clave* de la búsqueda. El tercer argumento es un puntero al elemento de la matriz que se va a comparar con la *clave*.

*contexto*\
Un puntero a un objeto al que se puede acceder en la función de comparación.

## <a name="return-value"></a>Valor devuelto

**bsearch_s** devuelve un puntero a una aparición de *clave* en la matriz a la que apunta la *base*. Si no se encuentra la *clave* , la función devuelve **null**. Si la matriz no está en orden ascendente o contiene registros duplicados con claves idénticas, el resultado es impredecible.

Si se pasan parámetros no válidos a la función, invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones del error

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*Compare*|*número*|*width*|**errno**|
|**ACEPTA**|cualquiera|cualquiera|cualquiera|cualquiera|**EINVAL**|
|cualquiera|**ACEPTA**|cualquiera|!= 0|cualquiera|**EINVAL**|
|cualquiera|cualquiera|cualquiera|cualquiera|= 0|**EINVAL**|
|cualquiera|cualquiera|**ACEPTA**|an|cualquiera|**EINVAL**|

## <a name="remarks"></a>Observaciones

La función **bsearch_s** realiza una búsqueda binaria de una matriz ordenada de elementos *numéricos* , cada uno de los cuales tiene un tamaño de bytes de *ancho* . El valor *base* es un puntero a la base de la matriz que se va a buscar y *key* es el valor que se busca. El parámetro *Compare* es un puntero a una rutina proporcionada por el usuario que compara la clave solicitada con un elemento de matriz y devuelve uno de los siguientes valores que especifican su relación:

|Valor devuelto por la rutina de *comparación*|Descripción|
|-----------------------------------------|-----------------|
|\< 0|El valor de clave es menor que el elemento de matriz.|
|0|El valor de clave es igual al elemento de matriz.|
|> 0|El valor de clave es mayor que el elemento de matriz.|

El puntero de *contexto* puede ser útil si la estructura de datos de búsqueda forma parte de un objeto y la función de comparación necesita acceder a los miembros del objeto. La función de *comparación* puede convertir el puntero void en el tipo de objeto adecuado y acceder a los miembros de ese objeto. La adición del parámetro de *contexto* hace que **bsearch_s** más seguro, ya que se puede utilizar contexto adicional para evitar errores de reentrada asociados al uso de variables estáticas para que los datos estén disponibles para la función de *comparación* .

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> y \<search.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa ordena una matriz de cadenas con [qsort_s](qsort-s.md) y luego usa bsearch_s para buscar la palabra "cat".

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
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
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
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

## <a name="see-also"></a>Consulta también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
