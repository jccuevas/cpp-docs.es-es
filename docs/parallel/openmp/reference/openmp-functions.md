---
title: Funciones de OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 1bf0e08f3b28368d9aea5438b3036ac8a0283735
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363094"
---
# <a name="openmp-functions"></a>Funciones de OpenMP

Proporciona vínculos a las funciones utilizadas en la API de OpenMP.

El objeto Visual C++ implementación del estándar OpenMP incluye los siguientes tipos de datos y funciones.

Para la ejecución del entorno:

|Función|Descripción|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Establece el número de subprocesos en próximas regiones en paralelo, a menos que se reemplaza por un [num_threads](openmp-clauses.md#num-threads) cláusula.|
|[omp_get_num_threads](#omp-get-num-threads)|Devuelve el número de subprocesos en la región paralela.|
|[omp_get_max_threads](#omp-get-max-threads)|Devuelve un entero que es igual o mayor que el número de subprocesos que estaría disponible si una región paralela sin [num_threads](openmp-clauses.md#num-threads) se definieron en ese momento en el código.|
|[omp_get_thread_num](#omp-get-thread-num)|Devuelve el número de subprocesos de la ejecución de subprocesos dentro de su equipo de subproceso.|
|[omp_get_num_procs](#omp-get-num-procs)|Devuelve el número de procesadores que están disponibles cuando se llama a la función.|
|[omp_in_parallel](#omp-in-parallel)|Devuelve cero si se llama desde dentro de una región paralela.|
|[omp_set_dynamic](#omp-set-dynamic)|Indica que el número de subprocesos disponibles en próximas regiones en paralelo puede ser ajustado por el tiempo de ejecución.|
|[omp_get_dynamic](#omp-get-dynamic)|Devuelve un valor que indica si el número de subprocesos disponibles en próximas regiones en paralelo puede ser ajustado por el tiempo de ejecución.|
|[omp_set_nested](#omp-set-nested)|Habilita el paralelismo anidado.|
|[omp_get_nested](#omp-get-nested)|Devuelve un valor que indica si está habilitado el paralelismo anidado.|

Bloqueo:

|Función|Descripción|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicializa un bloqueo simple.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicializa un bloqueo.|
|[omp_destroy_lock](#omp-destroy-lock)|Anula la inicialización de un bloqueo.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Anula la inicialización de un bloqueo anidable.|
|[omp_set_lock](#omp-set-lock)|Bloques de ejecución de subprocesos hasta que esté disponible un bloqueo.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Bloques de ejecución de subprocesos hasta que esté disponible un bloqueo.|
|[omp_unset_lock](#omp-unset-lock)|Libera un bloqueo.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Libera un bloqueo anidable.|
|[omp_test_lock](#omp-test-lock)|Intenta establecer un bloqueo, pero no bloquea la ejecución de subprocesos.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Intenta establecer un bloqueo anidable pero no bloquea la ejecución de subprocesos.|

|Tipo de datos|Descripción|
|---------|-----------|
|`omp_lock_t`|Un tipo que contiene el estado de un bloqueo, si el bloqueo esté disponible o si un subproceso posee un bloqueo.|
|`omp_nest_lock_t`|Un tipo que contiene uno de los siguientes fragmentos de información sobre un bloqueo: si el bloqueo esté disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.|

Para las rutinas de control de tiempo:

|Función|Descripción|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Devuelve que un valor en segundos del tiempo transcurrido en algún momento.|
|[omp_get_wtick](#omp-get-wtick)|Devuelve el número de segundos entre ciclos de reloj de procesador.|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

Anula la inicialización de un bloqueo.

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_lock_t` que se inicializó con [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.2 omp_destroy_lock y omp_destroy_nest_lock funciones](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_lock](#omp-init-lock) para obtener un ejemplo del uso de `omp_destroy_lock`.

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Anula la inicialización de un bloqueo anidable.

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_nest_lock_t` que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.2 omp_destroy_lock y omp_destroy_nest_lock funciones](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_nest_lock](#omp-init-nest-lock) para obtener un ejemplo del uso de `omp_destroy_nest_lock`.

## <a name="omp-get-dynamic"></a>omp_get_dynamic

Devuelve un valor que indica si el número de subprocesos disponibles en próximas regiones en paralelo puede ser ajustado por el tiempo de ejecución.

```
int omp_get_dynamic();
```

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero significa que se ajustará dinámicamente los subprocesos.

### <a name="remarks"></a>Comentarios

Realizar un ajuste dinámico de subprocesos se especifica con [omp_set_dynamic ()](#omp-set-dynamic) y [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Para obtener más información, consulte [3.1.7 omp_set_dynamic () función](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_set_dynamic ()](#omp-set-dynamic) para obtener un ejemplo del uso de `omp_get_dynamic`.

## <a name="omp-get-max-threads"></a>omp_get_max_threads

Devuelve un entero que es igual o mayor que el número de subprocesos que estaría disponible si una región paralela sin [num_threads](openmp-clauses.md#num-threads) se definieron en ese momento en el código.

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.3 omp_get_max_threads () función](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp-get-nested"></a>omp_get_nested

Devuelve un valor que indica si está habilitado el paralelismo anidado.

```
int omp_get_nested( );
```

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero significa que se habilita el paralelismo anidado.

### <a name="remarks"></a>Comentarios

Paralelismo anidado se especifica con [omp_set_nested ()](#omp-set-nested) y [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Para obtener más información, consulte [3.1.10 omp_get_nested () función](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_set_nested ()](#omp-set-nested) para obtener un ejemplo del uso de `omp_get_nested`.

## <a name="omp-get-num-procs"></a>omp_get_num_procs

Devuelve el número de procesadores que están disponibles cuando se llama a la función.

```
int omp_get_num_procs();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.5 omp_get_num_procs () función](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp-get-num-threads"></a>omp_get_num_threads

Devuelve el número de subprocesos en la región paralela.

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.2 omp_get_num_threads () función](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp-get-thread-num"></a>omp_get_thread_num

Devuelve el número de subprocesos de la ejecución de subprocesos dentro de su equipo de subproceso.

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.4 omp_get_thread_num () función](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Ejemplo

Consulte [paralelo](openmp-directives.md#parallel) para obtener un ejemplo del uso de `omp_get_thread_num`.

## <a name="omp-get-wtick"></a>omp_get_wtick

Devuelve el número de segundos entre ciclos de reloj de procesador.

```
double omp_get_wtick( );
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.3.2 omp_get_wtick () función](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_get_wtime ()](#omp-get-wtime) para obtener un ejemplo del uso de `omp_get_wtick`.

## <a name="omp-get-wtime"></a>omp_get_wtime

Devuelve que un valor en segundos del tiempo transcurrido en algún momento.

```
double omp_get_wtime( );
```

### <a name="return-value"></a>Valor devuelto

Devuelve que un valor en segundos del tiempo transcurrido desde el punto de algunos arbitrario, pero coherente.

### <a name="remarks"></a>Comentarios

Ese punto seguirá siendo coherente durante la ejecución del programa, realizar comparaciones próximas posibles.

Para obtener más información, consulte [3.3.1 omp_get_wtime () función](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp-in-parallel"></a>omp_in_parallel

Devuelve cero si se llama desde dentro de una región paralela.

```
int omp_in_parallel( );
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.6 omp_in_parallel () función](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp-init-lock"></a>omp_init_lock

Inicializa un bloqueo simple.

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_lock_t`.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.1 omp_init_lock y omp_init_nest_lock funciones](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

Inicializa un bloqueo.

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_nest_lock_t`.

### <a name="remarks"></a>Comentarios

El recuento inicial de anidamiento es cero.

Para obtener más información, consulte [3.2.1 omp_init_lock y omp_init_nest_lock funciones](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp-set-dynamic"></a>omp_set_dynamic

Indica que el número de subprocesos disponibles en próximas regiones en paralelo puede ser ajustado por el tiempo de ejecución.

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parámetros

*val*<br/>
Un valor que indica si el número de subprocesos disponibles en próximas regiones en paralelo puede ser ajustado por el tiempo de ejecución. Si es distinto de cero, que el tiempo de ejecución puede ajustar el número de subprocesos, si es cero, el tiempo de ejecución no ajustar dinámicamente el número de subprocesos.

### <a name="remarks"></a>Comentarios

El número de subprocesos nunca superará el valor establecido por [omp_set_num_threads ()](#omp-set-num-threads) o [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Use [omp_get_dynamic ()](#omp-get-dynamic) para mostrar la configuración actual de `omp_set_dynamic`.

La configuración de `omp_set_dynamic` reemplazará la configuración de la [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) variable de entorno.

Para obtener más información, consulte [3.1.7 omp_set_dynamic () función](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-lock"></a>omp_set_lock

Bloques de ejecución de subprocesos hasta que esté disponible un bloqueo.

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_lock_t` que se inicializó con [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.3 omp_set_lock y omp_set_nest_lock funciones](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Ejemplos

Consulte [omp_init_lock](#omp-init-lock) para obtener un ejemplo del uso de `omp_set_lock`.

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

Bloques de ejecución de subprocesos hasta que esté disponible un bloqueo.

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_nest_lock_t` que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.3 omp_set_lock y omp_set_nest_lock funciones](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Ejemplos

Consulte [omp_init_nest_lock](#omp-init-nest-lock) para obtener un ejemplo del uso de `omp_set_nest_lock`.

## <a name="omp-set-nested"></a>omp_set_nested

Habilita el paralelismo anidado.

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parámetros

*val*<br/>
Un valor distinto de cero habilita el paralelismo anidado, aunque cero deshabilita el paralelismo anidado.

### <a name="remarks"></a>Comentarios

OMP anidado paralelismo puede activarse con `omp_set_nested`, o estableciendo la [OMP_NESTED](openmp-environment-variables.md#omp-nested) variable de entorno.

La configuración de `omp_set_nested` reemplazará la configuración de la `OMP_NESTED` variable de entorno.

Habilitación de la variable de entorno puede interrumpir un programa operativo en caso contrario, ya que aumenta exponencialmente el número de subprocesos cuando se anidan regiones en paralelo. Por ejemplo, una función que se repite seis veces con el número de subprocesos OMP establecido en 4 requiere 4096 (4 a la potencia de 6) subprocesos. Excepto con las aplicaciones dependientes de E/s, el rendimiento de una aplicación generalmente es peor si hay más subprocesos que procesadores.

Use [omp_get_nested ()](#omp-get-nested) para mostrar la configuración actual de `omp_set_nested`.

Para obtener más información, consulte [3.1.9 omp_set_nested () función](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-num-threads"></a>omp_set_num_threads

Establece el número de subprocesos en próximas regiones en paralelo, a menos que se reemplaza por un [num_threads](openmp-clauses.md#num-threads) cláusula.

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parámetros

*num_threads*<br/>
El número de subprocesos en la región paralela.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.1 omp_set_num_threads () función](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_get_num_threads ()](#omp-get-num-threads) para obtener un ejemplo del uso de `omp_set_num_threads`.

## <a name="omp-test-lock"></a>omp_test_lock

Intenta establecer un bloqueo, pero no bloquea la ejecución de subprocesos.

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_lock_t` que se inicializó con [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.5 omp_test_lock y omp_test_nest_lock funciones](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

Intenta establecer un bloqueo anidable pero no bloquea la ejecución de subprocesos.

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_nest_lock_t` que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.5 omp_test_lock y omp_test_nest_lock funciones](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp-unset-lock"></a>omp_unset_lock

Libera un bloqueo.

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_lock_t` que se inicializó con [omp_init_lock](#omp-init-lock), que se poseen el subproceso y ejecuta en la función.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.4 omp_unset_lock y omp_unset_nest_lock funciones](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_lock](#omp-init-lock) para obtener un ejemplo del uso de `omp_unset_lock`.

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Libera un bloqueo anidable.

```
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Una variable de tipo `omp_nest_lock_t` que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock), que se poseen el subproceso y ejecuta en la función.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.2.4 omp_unset_lock y omp_unset_nest_lock funciones](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_nest_lock](#omp-init-nest-lock) para obtener un ejemplo del uso de `omp_unset_nest_lock`.
