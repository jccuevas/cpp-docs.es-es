---
title: qsort_s
ms.date: 4/2/2020
api_name:
- qsort_s
- _o_qsort_s
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
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: 934801531804345a8cede6ed1ac4abb06bae45b4
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913275"
---
# <a name="qsort_s"></a>qsort_s

Realiza una ordenación rápida. Versión de [qsort](qsort.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
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
Función de comparación. El primer argumento es el puntero de *contexto* . El segundo argumento es un puntero a la *clave* de la búsqueda. El tercer argumento es un puntero al elemento de la matriz que se va a comparar con la *clave*.

*contextoo*<br/>
Un puntero a un contexto, que puede ser cualquier objeto al que la rutina de *comparación* necesite tener acceso.

## <a name="remarks"></a>Observaciones

La función **qsort_s** implementa un algoritmo de ordenación rápida para ordenar una matriz de elementos *numéricos* , cada uno de los bytes de *ancho* . La *base* del argumento es un puntero a la base de la matriz que se va a ordenar. **qsort_s** sobrescribe esta matriz con los elementos ordenados. El argumento *Compare* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación. **qsort_s** llama a la rutina de *comparación* una o más veces durante la ordenación, pasando punteros a dos elementos de la matriz en cada llamada:

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

La rutina debe comparar los elementos y luego devolver uno de los siguientes valores:

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|**Elem1** menor que **Elem2**|
|0|**Elem1** equivalente a **Elem2**|
|> 0|**Elem1** mayor que **Elem2**|

La matriz se clasifica en orden ascendente, de acuerdo con la función de comparación. Para clasificar una matriz en orden decreciente, invierta el sentido de "mayor que" y "menor que" en la función de comparación.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve y **errno** se establece en **EINVAL**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="error-conditions"></a>Condiciones de error

|key|base|compare|num|width|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**ACEPTA**|cualquiera|cualquiera|cualquiera|cualquiera|**EINVAL**|
|cualquiera|**ACEPTA**|cualquiera|!= 0|cualquiera|**EINVAL**|
|cualquiera|cualquiera|cualquiera|cualquiera|<= 0|**EINVAL**|
|cualquiera|cualquiera|**ACEPTA**|cualquiera|cualquiera|**EINVAL**|

**qsort_s** tiene el mismo comportamiento que **qsort** pero tiene el parámetro de *contexto* y establece **errno**. Al pasar un parámetro de *contexto* , las funciones de comparación pueden utilizar un puntero de objeto para tener acceso a la funcionalidad del objeto u otra información no accesible a través de un puntero de elemento. La adición del parámetro de *contexto* hace **qsort_s** más seguro porque el *contexto* se puede usar para evitar errores de reentrada introducidos mediante variables estáticas para que la información compartida esté disponible para la función de *comparación* .

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h> y \<search.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** todas las versiones de las [características de la biblioteca de CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el parámetro *Context* en la función **qsort_s** . El parámetro *Context* facilita la realización de ordenaciones seguras para subprocesos. En lugar de usar variables estáticas que se deben sincronizar para garantizar la seguridad para subprocesos, pase un parámetro de *contexto* diferente en cada orden. En este ejemplo, se usa un objeto de configuración regional como parámetro de *contexto* .

```cpp
// crt_qsort_s.cpp
// compile with: /EHsc /MT
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4
// is the n tilde.

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.850"
#define SPANISH_LOCALE "Spanish_Spain.850"
#define ENGLISH_LOCALE "English_US.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S and \x001f for the n tilde.
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.1252"
#define SPANISH_LOCALE "Spanish_Spain.1252"
#define ENGLISH_LOCALE "English_US.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making sort_array vulnerable to thread
// conflicts.

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char s1[256];
    char s2[256];
    strcpy_s(s1, 256, *(char**)str1);
    strcpy_s(s2, 256, *(char**)str2);
    _strlwr_s( s1, sizeof(s1) );
    _strlwr_s( s2, sizeof(s2) );

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(s1,
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);

}

void sort_array(char *array[], int num, locale &loc)
{
    qsort_s(array, num, sizeof(char*), compare, &loc);
}

void print_array(char *a[], int c)
{
   for (int i = 0; i < c; i++)
      printf("%s ", a[i]);
   printf("\n");

}

void sort_german(void * Dummy)
{
   sort_array(array1, 6, locale(GERMAN_LOCALE));
}

void sort_spanish(void * Dummy)
{
   sort_array(array2, 3, locale(SPANISH_LOCALE));
}

void sort_english(void * Dummy)
{
   sort_array(array3, 3, locale(ENGLISH_LOCALE));
}

int main( )
{
   int i;
   HANDLE threads[3];

   printf("Unsorted input:\n");
   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);

   // Create several threads that perform sorts in different
   // languages at the same time.

   threads[0] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_german , 0, NULL));
   threads[1] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_spanish, 0, NULL));
   threads[2] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_english, 0, NULL));

   for (i = 0; i < 3; i++)
   {
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
      {
         printf("Error creating threads.\n");
         exit(1);
      }
   }

   // Wait until all threads have terminated.
   WaitForMultipleObjects(3, threads, true, INFINITE);

   printf("Sorted output: \n");

   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);
}
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>Consulta también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
