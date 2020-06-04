---
title: 3. Funciones de biblioteca en tiempo de ejecución
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370282"
---
# <a name="3-run-time-library-functions"></a>3. Funciones de biblioteca en tiempo de ejecución

En esta sección se describen las funciones de biblioteca en tiempo de ejecución de OpenMP C y C++. El ** \<encabezado omp.h>** declara dos tipos, varias funciones que se pueden utilizar para controlar y consultar el entorno de ejecución en paralelo, y bloquear funciones que se pueden usar para sincronizar el acceso a los datos.

El `omp_lock_t` tipo es un tipo de objeto capaz de representar que un bloqueo está disponible o que un subproceso posee un bloqueo. Estos bloqueos se conocen como *bloqueos simples.*

El `omp_nest_lock_t` tipo es un tipo de objeto capaz de representar que un bloqueo está disponible, o tanto la identidad del subproceso que posee el bloqueo como un recuento de *anidamiento* (descrito a continuación). Estos bloqueos se conocen como *bloqueos anidados.*

Las funciones de la biblioteca son funciones externas con vinculación "C".

Las descripciones de este capítulo se dividen en los siguientes temas:

- [Funciones del entorno de ejecución](#31-execution-environment-functions)
- [Funciones de bloqueo](#32-lock-functions)
- [Rutinas de temporización](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 Funciones del entorno de ejecución

Las funciones descritas en esta sección afectan y supervisan subprocesos, procesadores y el entorno paralelo:

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 función omp_set_num_threads

La `omp_set_num_threads` función establece el número predeterminado de subprocesos que `num_threads` se usará para regiones paralelas posteriores que no especifican una cláusula. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

El valor del parámetro *num_threads* debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para obtener un conjunto completo de `omp_set_num_threads` reglas sobre la interacción entre la función y el ajuste dinámico de subprocesos, consulte la [sección 2.3](2-directives.md#23-parallel-construct).

Esta función tiene los efectos descritos anteriormente `omp_in_parallel` cuando se llama desde una parte del programa donde la función devuelve cero. Si se llama desde una parte del `omp_in_parallel` programa donde la función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene `OMP_NUM_THREADS` prioridad sobre la variable de entorno. El valor predeterminado para el número de subprocesos, `omp_set_num_threads` que se puede establecer mediante una llamada o estableciendo la `OMP_NUM_THREADS` variable de entorno, se puede invalidar explícitamente en una sola `parallel` directiva especificando la `num_threads` cláusula.

Para obtener más información, consulte [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Referencias cruzadas

- [función omp_set_dynamic](#317-omp_set_dynamic-function)
- [función omp_get_dynamic](#318-omp_get_dynamic-function)
- [variable](4-environment-variables.md#42-omp_num_threads) de entorno OMP_NUM_THREADS
- [cláusula num_threads](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 función omp_get_num_threads

La `omp_get_num_threads` función devuelve el número de subprocesos que se encuentran actualmente en el equipo que ejecuta la región paralela desde la que se llama. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

La `num_threads` cláusula, `omp_set_num_threads` la función y la `OMP_NUM_THREADS` variable de entorno controlan el número de subprocesos de un equipo.

Si el usuario no ha establecido explícitamente el número de subprocesos, el valor predeterminado es definido por la implementación. Esta función se enlaza a `parallel` la directiva envolvente más cercana. Si se llama desde una parte serial de un programa, o desde una región paralela anidada que se serializa, esta función devuelve 1.

Para obtener más información, consulte [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Referencias cruzadas

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 función omp_get_max_threads

La `omp_get_max_threads` función devuelve un entero que se garantiza que es al menos tan grande como el número `num_threads` de subprocesos que se usarían para formar un equipo si una región paralela sin una cláusula se viera en ese momento del código. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

A continuación se expresa un límite `omp_get_max_threads`inferior en el valor de:

> *hilos utilizados para el siguiente equipo* <= `omp_get_max_threads`

Tenga en cuenta que `num_threads` si otra región paralela utiliza la cláusula para solicitar un `omp_get_max_threads` número específico de subprocesos, la garantía en el límite inferior del resultado de ya no se mantiene.

El `omp_get_max_threads` valor devuelto de la función se puede utilizar para asignar dinámicamente almacenamiento suficiente para todos los subprocesos del equipo formado en la siguiente región paralela.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 función omp_get_thread_num

La `omp_get_thread_num` función devuelve el número de subproceso, dentro de su equipo, del subproceso que ejecuta la función. El número de subproceso `omp_get_num_threads()`se encuentra entre 0 y -1, ambos inclusive. El subproceso maestro del equipo es el subproceso 0.

El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Si se llama desde `omp_get_thread_num` una región serie, devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.

#### <a name="cross-references"></a>Referencias cruzadas

- [función omp_get_num_threads](#312-omp_get_num_threads-function)

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 función omp_get_num_procs

La `omp_get_num_procs` función devuelve el número de procesadores que están disponibles para el programa en el momento en que se llama a la función. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 función omp_in_parallel

La `omp_in_parallel` función devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela que se ejecuta en paralelo; de lo contrario, devuelve 0. El formato es como sigue:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecuta en paralelo, incluidas las regiones anidadas que se serializan.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 Función omp_set_dynamic

La `omp_set_dynamic` función habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de regiones paralelas. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* se evalúa como un valor distinto de cero, el entorno en tiempo de ejecución puede ajustar automáticamente el número de subprocesos que se usan para ejecutar las próximas regiones paralelas para utilizar mejor los recursos del sistema. Como consecuencia, el número de subprocesos especificado por el usuario es el número máximo de subprocesos. El número de subprocesos del equipo que ejecuta una región paralela permanece fijo `omp_get_num_threads` durante la duración de esa región paralela y la función lo notifica.

Si *dynamic_threads* se evalúa como 0, el ajuste dinámico está deshabilitado.

Esta función tiene los efectos descritos anteriormente `omp_in_parallel` cuando se llama desde una parte del programa donde la función devuelve cero. Si se llama desde una parte del `omp_in_parallel` programa donde la función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Una llamada `omp_set_dynamic` a tiene `OMP_DYNAMIC` prioridad sobre la variable de entorno.

El valor predeterminado para el ajuste dinámico de subprocesos está definido por la implementación. Como resultado, los códigos de usuario que dependen de un número específico de subprocesos para la ejecución correcta deben deshabilitar explícitamente los subprocesos dinámicos. Las implementaciones no son necesarias para proporcionar la capacidad de ajustar dinámicamente el número de subprocesos, pero se requieren para proporcionar la interfaz para admitir la portabilidad en todas las plataformas.

#### <a name="microsoft-specific"></a>Específico de Microsoft

El soporte `omp_get_dynamic` actual `omp_set_dynamic` de y es el siguiente:

El parámetro `omp_set_dynamic` de entrada no afecta a la directiva de subprocesos y no cambia el número de subprocesos. `omp_get_num_threads`siempre devuelve el número definido por el usuario, si se establece, o el número de subproceso predeterminado. En la implementación `omp_set_dynamic(0)` actual de Microsoft, desactiva el subproceso dinámico para que el conjunto existente de subprocesos se pueda reutilizar para la siguiente región paralela. `omp_set_dynamic(1)`activa el subproceso dinámico descartando el conjunto existente de subprocesos y creando un nuevo conjunto para la próxima región paralela. El número de subprocesos del nuevo conjunto es el mismo que el `omp_get_num_threads`conjunto anterior y se basa en el valor devuelto de . Por lo tanto, `omp_set_dynamic(0)` para obtener el mejor rendimiento, utilice para reutilizar los subprocesos existentes.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 función omp_get_dynamic

La `omp_get_dynamic` función devuelve un valor distinto de cero si el ajuste dinámico de subprocesos está habilitado y devuelve 0 en caso contrario. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Si la implementación no implementa el ajuste dinámico del número de subprocesos, esta función siempre devuelve 0. Para obtener más información, consulte [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Referencias cruzadas

- Para obtener una descripción del ajuste dinámico de subprocesos, consulte [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 Función omp_set_nested

La `omp_set_nested` función habilita o deshabilita el paralelismo anidado. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Si *anidado* se evalúa como 0, el paralelismo anidado está deshabilitado, que es el valor predeterminado, y las regiones paralelas anidadas se serializan y ejecutan mediante el subproceso actual. De lo contrario, se habilita el paralelismo anidado y las regiones paralelas anidadas pueden implementar subprocesos adicionales para formar equipos anidados.

Esta función tiene los efectos descritos anteriormente `omp_in_parallel` cuando se llama desde una parte del programa donde la función devuelve cero. Si se llama desde una parte del `omp_in_parallel` programa donde la función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene `OMP_NESTED` prioridad sobre la variable de entorno.

Cuando se habilita el paralelismo anidado, el número de subprocesos utilizados para ejecutar regiones paralelas anidadas está definido por la implementación. Como resultado, las implementaciones compatibles con OpenMP pueden serializar regiones paralelas anidadas incluso cuando se habilita el paralelismo anidado.

#### <a name="cross-references"></a>Referencias cruzadas

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 función omp_get_nested

La `omp_get_nested` función devuelve un valor distinto de cero si el paralelismo anidado está habilitado y 0 si está deshabilitado. Para obtener más información sobre el paralelismo anidado, consulte [omp_set_nested](#319-omp_set_nested-function). El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Si una implementación no implementa el paralelismo anidado, esta función siempre devuelve 0.

## <a name="32-lock-functions"></a>3.2 Funciones de bloqueo

Las funciones descritas en esta sección manipulan los bloqueos utilizados para la sincronización.

Para las siguientes funciones, la `omp_lock_t`variable de bloqueo debe tener el tipo . Solo se debe tener acceso a esta variable a través de estas funciones. Todas las funciones de bloqueo `omp_lock_t` requieren un argumento que tenga un puntero al tipo.

- La función [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicializa un bloqueo simple.
- La función [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) elimina un bloqueo simple.
- La función [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) espera hasta que haya un bloqueo simple disponible.
- La función [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libera un bloqueo simple.
- La función [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) prueba un bloqueo simple.

Para las siguientes funciones, la `omp_nest_lock_t`variable de bloqueo debe tener el tipo .  Solo se debe tener acceso a esta variable a través de estas funciones. Todas las funciones de bloqueo anidadas `omp_nest_lock_t` requieren un argumento que tenga un puntero al tipo.

- La función [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicializa un bloqueo anidado.
- La función [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) elimina un bloqueo anidado.
- La función [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) espera hasta que haya disponible un bloqueo anidado.
- La función [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libera un bloqueo anidado.
- La función [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) prueba un bloqueo anidado.

Las funciones de bloqueo OpenMP acceden a la variable de bloqueo de forma que siempre leen y actualizan el valor más actual de la variable de bloqueo. Por lo tanto, no es necesario que `flush` un programa OpenMP incluya directivas explícitas para asegurarse de que el valor de la variable de bloqueo es coherente entre diferentes subprocesos. (Puede ser necesario `flush` que las directivas hagan que los valores de otras variables sean coherentes.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 funciones omp_init_lock y omp_init_nest_lock

Estas funciones proporcionan el único medio de inicializar un bloqueo. Cada función inicializa el bloqueo asociado con el *bloqueo* de parámetros para su uso en las próximas llamadas. El formato es como sigue:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

El estado inicial está desbloqueado (es decir, ningún subproceso posee el bloqueo). Para un bloqueo anidado, el recuento de anidamiento inicial es cero. No es conforme llamar a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 funciones omp_destroy_lock y omp_destroy_nest_lock

Estas funciones se aseguran de que el *bloqueo* de variable sin inicializar. El formato es como sigue:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

No es conforme llamar a cualquiera de estas rutinas con una variable de bloqueo que no está inicializada o desbloqueada.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 funciones omp_set_lock y omp_set_nest_lock

Cada una de estas funciones bloquea el subproceso que ejecuta la función hasta que el bloqueo especificado está disponible y, a continuación, establece el bloqueo. Un bloqueo simple está disponible si está desbloqueado. Un bloqueo anidado está disponible si está desbloqueado o si ya es propiedad del subproceso que ejecuta la función. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Para un bloqueo simple, `omp_set_lock` el argumento de la función debe apuntar a una variable de bloqueo inicializada. La propiedad del bloqueo se concede al subproceso que ejecuta la función.

Para un bloqueo anidado, el `omp_set_nest_lock` argumento de la función debe apuntar a una variable de bloqueo inicializada. El recuento de anidamiento se incrementa y el subproceso se concede o mantiene la propiedad del bloqueo.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 funciones omp_unset_lock y omp_unset_nest_lock

Estas funciones proporcionan los medios para liberar la propiedad de un bloqueo. El formato es como sigue:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

El argumento de cada una de estas funciones debe apuntar a una variable de bloqueo inicializada propiedad del subproceso que ejecuta la función. El comportamiento es indefinido si el subproceso no posee ese bloqueo.

Para un bloqueo `omp_unset_lock` simple, la función libera el subproceso que ejecuta la función de la propiedad del bloqueo.

Para un bloqueo anidado, la `omp_unset_nest_lock` función disminuye el recuento de anidamiento y libera el subproceso que ejecuta la función de la propiedad del bloqueo si el recuento resultante es cero.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 funciones omp_test_lock y omp_test_nest_lock

Estas funciones intentan establecer un bloqueo, pero no bloquean la ejecución del subproceso. El formato es como sigue:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

El argumento debe apuntar a una variable de bloqueo inicializada. Estas funciones intentan establecer un bloqueo `omp_set_lock` `omp_set_nest_lock`de la misma manera que y , excepto que no bloquean la ejecución del subproceso.

Para un bloqueo `omp_test_lock` simple, la función devuelve un valor distinto de cero si el bloqueo se establece correctamente; de lo contrario, devuelve cero.

Para un bloqueo anidado, la `omp_test_nest_lock` función devuelve el nuevo recuento de anidamiento si el bloqueo se establece correctamente; de lo contrario, devuelve cero.

## <a name="33-timing-routines"></a>3.3 Rutinas de temporización

Las funciones descritas en esta sección soportan un temporizador portátil del reloj de pared:

- La función [omp_get_wtime](#331-omp_get_wtime-function) devuelve el tiempo de reloj de pared transcurrido.
- La función [omp_get_wtick](#332-omp_get_wtick-function) devuelve segundos entre los ticks de reloj sucesivos.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 función omp_get_wtime

La `omp_get_wtime` función devuelve un valor de punto flotante de doble precisión igual al tiempo de reloj de pared transcurrido en segundos ya que algún "tiempo en el pasado".  El "tiempo en el pasado" real es arbitrario, pero se garantiza que no cambiará durante la ejecución del programa de aplicación. El formato es como sigue:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Se ha previsto que la función se utilizará para medir los tiempos transcurridos como se muestra en el ejemplo siguiente:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Las horas devueltas son "tiempos por subproceso" por lo que significa que no es necesario que sean coherentes globalmente en todos los subprocesos que participan en una aplicación.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 función omp_get_wtick

La `omp_get_wtick` función devuelve un valor de punto flotante de doble precisión igual al número de segundos entre los tictaces de reloj sucesivos. El formato es como sigue:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
