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
ms.openlocfilehash: 0475a83ba259ed00bbcb9ddaba99a1556b35f613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317136"
---
# <a name="openmp-functions"></a>Funciones de OpenMP

Proporciona vínculos a funciones utilizadas en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye las siguientes funciones y tipos de datos.

Para la ejecución del entorno:

|Función|Descripción|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Establece el número de subprocesos en las próximas regiones paralelas, a menos que se invalide mediante una cláusula [num_threads.](openmp-clauses.md#num-threads)|
|[omp_get_num_threads](#omp-get-num-threads)|Devuelve el número de subprocesos de la región paralela.|
|[omp_get_max_threads](#omp-get-max-threads)|Devuelve un entero que es igual o mayor que el número de subprocesos que estarían disponibles si una región paralela sin [num_threads](openmp-clauses.md#num-threads) se definieran en ese punto del código.|
|[omp_get_thread_num](#omp-get-thread-num)|Devuelve el número de subproceso del subproceso que se ejecuta dentro de su equipo de subprocesos.|
|[omp_get_num_procs](#omp-get-num-procs)|Devuelve el número de procesadores que están disponibles cuando se llama a la función.|
|[omp_in_parallel](#omp-in-parallel)|Devuelve distinto de cero si se llama desde dentro de una región paralela.|
|[omp_set_dynamic](#omp-set-dynamic)|Indica que el número de subprocesos disponibles en las próximas regiones paralelas se puede ajustar por el tiempo de ejecución.|
|[omp_get_dynamic](#omp-get-dynamic)|Devuelve un valor que indica si el número de subprocesos disponibles en las próximas regiones paralelas se puede ajustar en tiempo de ejecución.|
|[omp_set_nested](#omp-set-nested)|Habilita el paralelismo anidado.|
|[omp_get_nested](#omp-get-nested)|Devuelve un valor que indica si el paralelismo anidado está habilitado.|

Para bloqueo:

|Función|Descripción|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicializa un bloqueo simple.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicializa un bloqueo.|
|[omp_destroy_lock](#omp-destroy-lock)|Uninitializes un bloqueo.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Uninitializes un bloqueo anidado.|
|[omp_set_lock](#omp-set-lock)|Bloquea la ejecución de subprocesos hasta que haya un bloqueo disponible.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Bloquea la ejecución de subprocesos hasta que haya un bloqueo disponible.|
|[omp_unset_lock](#omp-unset-lock)|Libera un bloqueo.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Libera un bloqueo anidado.|
|[omp_test_lock](#omp-test-lock)|Intenta establecer un bloqueo, pero no bloquea la ejecución de subprocesos.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Intenta establecer un bloqueo anidado, pero no bloquea la ejecución de subprocesos.|

|Tipo de datos|Descripción|
|---------|-----------|
|`omp_lock_t`|Tipo que contiene el estado de un bloqueo, si el bloqueo está disponible o si un subproceso posee un bloqueo.|
|`omp_nest_lock_t`|Tipo que contiene uno de los siguientes elementos de información sobre un bloqueo: si el bloqueo está disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.|

Para rutinas de temporización:

|Función|Descripción|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Devuelve un valor en segundos del tiempo transcurrido desde algún punto.|
|[omp_get_wtick](#omp-get-wtick)|Devuelve el número de segundos entre los ticks del reloj del procesador.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a>omp_destroy_lock

Uninitializes un bloqueo.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_lock_t` tipo que se inicializó con [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.2 funciones de omp_destroy_lock y omp_destroy_nest_lock](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_lock](#omp-init-lock) para obtener `omp_destroy_lock`un ejemplo del uso de .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Uninitializes un bloqueo anidado.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_nest_lock_t` tipo que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.2 funciones de omp_destroy_lock y omp_destroy_nest_lock](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_nest_lock](#omp-init-nest-lock) para obtener `omp_destroy_nest_lock`un ejemplo de uso de .

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a>omp_get_dynamic

Devuelve un valor que indica si el número de subprocesos disponibles en las próximas regiones paralelas se puede ajustar en tiempo de ejecución.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero significa que los subprocesos se ajustarán dinámicamente.

### <a name="remarks"></a>Observaciones

El ajuste dinámico de subprocesos se especifica con [omp_set_dynamic](#omp-set-dynamic) y [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Para obtener más información, consulte [3.1.7 omp_set_dynamic función](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_set_dynamic](#omp-set-dynamic) para obtener `omp_get_dynamic`un ejemplo de uso de .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a>omp_get_max_threads

Devuelve un entero que es igual o mayor que el número de subprocesos que estarían disponibles si una región paralela sin [num_threads](openmp-clauses.md#num-threads) se definieran en ese punto del código.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.1.3 omp_get_max_threads (función)](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a>omp_get_nested

Devuelve un valor que indica si el paralelismo anidado está habilitado.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero significa que el paralelismo anidado está habilitado.

### <a name="remarks"></a>Observaciones

El paralelismo anidado se especifica con [omp_set_nested](#omp-set-nested) y [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Para obtener más información, consulte [3.1.10 omp_get_nested función](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_set_nested](#omp-set-nested) para obtener `omp_get_nested`un ejemplo de uso de .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a>omp_get_num_procs

Devuelve el número de procesadores que están disponibles cuando se llama a la función.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.1.5 omp_get_num_procs (función) de la omp_get_num_procs](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

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

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a>omp_get_num_threads

Devuelve el número de subprocesos de la región paralela.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.1.2 omp_get_num_threads (función) de omp_get_num_threads](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a>omp_get_thread_num

Devuelve el número de subproceso del subproceso que se ejecuta dentro de su equipo de subprocesos.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.1.4 omp_get_thread_num (función)](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Ejemplo

Consulte [paralelo](openmp-directives.md#parallel) para obtener `omp_get_thread_num`un ejemplo de uso de .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a>omp_get_wtick

Devuelve el número de segundos entre los ticks del reloj del procesador.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.3.2 omp_get_wtick función](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_get_wtime](#omp-get-wtime) para obtener `omp_get_wtick`un ejemplo de uso de .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a>omp_get_wtime

Devuelve un valor en segundos del tiempo transcurrido desde algún punto.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor en segundos del tiempo transcurrido desde algún punto arbitrario, pero coherente.

### <a name="remarks"></a>Observaciones

Ese punto seguirá siendo coherente durante la ejecución del programa, haciendo posibles las próximas comparaciones.

Para obtener más información, consulte [3.3.1 omp_get_wtime (función)](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)de omp_get_wtime .

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

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a>omp_in_parallel

Devuelve distinto de cero si se llama desde dentro de una región paralela.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.1.6 omp_in_parallel (función) .](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md)

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

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a>omp_init_lock

Inicializa un bloqueo simple.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Una variable de tipo `omp_lock_t`.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.1 funciones de omp_init_lock y omp_init_nest_lock](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a>omp_init_nest_lock

Inicializa un bloqueo.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Una variable de tipo `omp_nest_lock_t`.

### <a name="remarks"></a>Observaciones

El recuento inicial de anidamiento es cero.

Para obtener más información, consulte [3.2.1 funciones de omp_init_lock y omp_init_nest_lock](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a>omp_set_dynamic

Indica que el número de subprocesos disponibles en las próximas regiones paralelas se puede ajustar por el tiempo de ejecución.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parámetros

*Val*<br/>
Valor que indica si el tiempo de ejecución puede ajustar el número de subprocesos disponibles en las próximas regiones paralelas. Si es distinto de cero, el tiempo de ejecución puede ajustar el número de subprocesos, si es cero, el tiempo de ejecución no ajustará dinámicamente el número de subprocesos.

### <a name="remarks"></a>Observaciones

El número de subprocesos nunca superará el valor establecido por [omp_set_num_threads](#omp-set-num-threads) o por [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Utilice [omp_get_dynamic](#omp-get-dynamic) para mostrar `omp_set_dynamic`la configuración actual de .

La configuración `omp_set_dynamic` para invalidará la configuración de la variable de entorno [OMP_DYNAMIC.](openmp-environment-variables.md#omp-dynamic)

Para obtener más información, consulte [3.1.7 omp_set_dynamic función](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

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

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a>omp_set_lock

Bloquea la ejecución de subprocesos hasta que haya un bloqueo disponible.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_lock_t` tipo que se inicializó con [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.3 omp_set_lock y funciones de omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Ejemplos

Consulte [omp_init_lock](#omp-init-lock) para obtener `omp_set_lock`un ejemplo del uso de .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a>omp_set_nest_lock

Bloquea la ejecución de subprocesos hasta que haya un bloqueo disponible.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_nest_lock_t` tipo que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.3 omp_set_lock y funciones de omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Ejemplos

Consulte [omp_init_nest_lock](#omp-init-nest-lock) para obtener `omp_set_nest_lock`un ejemplo de uso de .

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a>omp_set_nested

Habilita el paralelismo anidado.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parámetros

*Val*<br/>
Un valor distinto de cero habilita el paralelismo anidado, mientras que cero deshabilita el paralelismo anidado.

### <a name="remarks"></a>Observaciones

El paralelismo anidado OMP `omp_set_nested`se puede activar con , o estableciendo la variable de entorno [OMP_NESTED.](openmp-environment-variables.md#omp-nested)

La configuración `omp_set_nested` para invalidará `OMP_NESTED` la configuración de la variable de entorno.

Habilitar la variable de entorno puede interrumpir un programa operativo de otro modo, porque el número de subprocesos aumenta exponencialmente al anidar regiones paralelas. Por ejemplo, una función que recurses seis veces con el número de subprocesos OMP establecido en 4 requiere 4.096 (4 a la potencia de 6) subprocesos. Excepto con las aplicaciones enlazadas a E/S, el rendimiento de una aplicación generalmente se degrada si hay más subprocesos que procesadores.

Utilice [omp_get_nested](#omp-get-nested) para mostrar `omp_set_nested`la configuración actual de .

Para obtener más información, consulte [3.1.9 omp_set_nested (función)](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)de omp_set_nested .

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

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a>omp_set_num_threads

Establece el número de subprocesos en las próximas regiones paralelas, a menos que se invalide mediante una cláusula [num_threads.](openmp-clauses.md#num-threads)

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parámetros

*num_threads*<br/>
El número de subprocesos en la región paralela.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.1.1 omp_set_num_threads función](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Ejemplo

Consulte [omp_get_num_threads](#omp-get-num-threads) para obtener `omp_set_num_threads`un ejemplo de uso de .

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a>omp_test_lock

Intenta establecer un bloqueo, pero no bloquea la ejecución de subprocesos.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_lock_t` tipo que se inicializó con [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.5 omp_test_lock y funciones de omp_test_nest_lock](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a>omp_test_nest_lock

Intenta establecer un bloqueo anidado, pero no bloquea la ejecución de subprocesos.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_nest_lock_t` tipo que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.5 omp_test_lock y funciones de omp_test_nest_lock](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a>omp_unset_lock

Libera un bloqueo.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_lock_t` tipo que se inicializó con [omp_init_lock](#omp-init-lock), propiedad del subproceso y que se ejecuta en la función.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.4 funciones de omp_unset_lock y omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_lock](#omp-init-lock) para obtener `omp_unset_lock`un ejemplo del uso de .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Libera un bloqueo anidado.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Variable de `omp_nest_lock_t` tipo que se inicializó con [omp_init_nest_lock](#omp-init-nest-lock), propiedad del subproceso y que se ejecuta en la función.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [3.2.4 funciones de omp_unset_lock y omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_nest_lock](#omp-init-nest-lock) para obtener `omp_unset_nest_lock`un ejemplo de uso de .
