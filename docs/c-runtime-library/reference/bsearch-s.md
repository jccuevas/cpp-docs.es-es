---
title: bsearch_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bsearch_s
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
- bsearch_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba025db097ffd9457024defa26fc29a5ae083e88
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="bsearchs"></a>bsearch_s

Realiza una búsqueda binaria de una matriz ordenada. Versión de [bsearch](bsearch.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de datos de búsqueda.

*Número*<br/>
Número de elementos.

*width*<br/>
Ancho de los elementos.

*compare*<br/>
Función de devolución de llamada que compara dos elementos. El primer argumento es el *contexto* puntero. El segundo argumento es un puntero a la *clave* para la búsqueda. El tercer argumento es un puntero al elemento de matriz que se comparará con *clave*.

*Contexto*<br/>
Un puntero a un objeto al que se puede acceder en la función de comparación.

## <a name="return-value"></a>Valor devuelto

**bsearch_s** devuelve un puntero a una instancia de *clave* en la matriz señalada por *base*. Si *clave* no se encuentra, la función devuelve **NULL**. Si la matriz no está en orden ascendente o contiene registros duplicados con claves idénticas, el resultado es impredecible.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones de error

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*compare*|*Número*|*width*|**errno**|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|= 0|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Comentarios

El **bsearch_s** función realiza una búsqueda binaria de una matriz ordenada de *número* elementos, cada uno de los *ancho* el tamaño en bytes. El *base* value es un puntero a la base de la matriz que desea buscar, y *clave* es el valor que se van a buscar. El *comparar* parámetro es un puntero a una rutina proporcionada por el usuario que compara la clave solicitada en un elemento de matriz y devuelve uno de los siguientes valores que especifica su relación:

|Valor devuelto por *comparar* rutina|Descripción|
|-----------------------------------------|-----------------|
|\< 0|El valor de clave es menor que el elemento de matriz.|
|0|El valor de clave es igual al elemento de matriz.|
|> 0|La clave es mayor que el elemento de matriz.|

El *contexto* puntero puede ser útil si la estructura de datos de búsqueda es parte de un objeto y la función de comparación necesita tener acceso a los miembros del objeto. El *comparar* función puede convertir el puntero void en los miembros de tipo y el acceso de objeto correspondiente de ese objeto. La adición de la *contexto* parámetro hace **bsearch_s** más seguro, ya que puede usarse contexto adicional para evitar errores de reentrada asociados con el uso de variables estáticas que estén disponibles para datos el *comparar* función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> y \<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
