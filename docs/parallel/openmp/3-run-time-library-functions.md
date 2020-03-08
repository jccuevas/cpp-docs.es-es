---
title: 3. Funciones de biblioteca en tiempo de ejecución
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 6155eb87bd7a1a0533caf99afb3db8417854df30
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882876"
---
# <a name="3-run-time-library-functions"></a>3. funciones de la biblioteca en tiempo de ejecución

En esta sección se describen las funciones C++ de la biblioteca en tiempo de ejecución y C de OpenMP. El encabezado **\<OMP. h >** declara dos tipos, varias funciones que se pueden usar para controlar y consultar el entorno de ejecución en paralelo, y funciones de bloqueo que se pueden usar para sincronizar el acceso a los datos.

El tipo `omp_lock_t` es un tipo de objeto capaz de representar que un bloqueo está disponible o que un subproceso posee un bloqueo. Estos bloqueos se denominan *bloqueos simples*.

El tipo `omp_nest_lock_t` es un tipo de objeto capaz de representar un bloqueo disponible, o bien la identidad del subproceso que posee el bloqueo y un *recuento de anidamiento* (se describe a continuación). Estos bloqueos se denominan *bloqueos anidables*.

Las funciones de biblioteca son funciones externas con vinculación "C".

Las descripciones de este capítulo se dividen en los temas siguientes:

- [Funciones de entorno de ejecución](#31-execution-environment-functions)
- [Lock (funciones)](#32-lock-functions)
- [Rutinas de tiempo](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3,1 funciones de entorno de ejecución

Las funciones descritas en esta sección afectan y supervisan los subprocesos, los procesadores y el entorno paralelo:

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads función)

La función `omp_set_num_threads` establece el número predeterminado de subprocesos que se van a usar para regiones paralelas posteriores que no especifican una cláusula `num_threads`. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

El valor del parámetro *num_threads* debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para obtener un conjunto completo de reglas sobre la interacción entre la función `omp_set_num_threads` y el ajuste dinámico de subprocesos, consulte la [sección 2,3](2-directives.md#23-parallel-construct).

Esta función tiene los efectos descritos anteriormente cuando se llama desde una parte del programa en la que la función `omp_in_parallel` devuelve cero. Si se llama desde una parte del programa en la que la función `omp_in_parallel` devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene prioridad sobre la variable de entorno `OMP_NUM_THREADS`. El valor predeterminado para el número de subprocesos, que se puede establecer llamando a `omp_set_num_threads` o estableciendo la variable de entorno `OMP_NUM_THREADS`, se puede invalidar explícitamente en una única directiva de `parallel` especificando la cláusula `num_threads`.

Para obtener más información, vea [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_set_dynamic](#317-omp_set_dynamic-function) función)
- [omp_get_dynamic](#318-omp_get_dynamic-function) función)
- Variable de entorno [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- cláusula [num_threads](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads función)

La función `omp_get_num_threads` devuelve el número de subprocesos actualmente en el equipo que ejecuta la región paralela desde la que se llama. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

La cláusula `num_threads`, la función `omp_set_num_threads` y la variable de entorno `OMP_NUM_THREADS` controlan el número de subprocesos de un equipo.

Si el usuario no ha establecido explícitamente el número de subprocesos, el valor predeterminado es definido por la implementación. Esta función se enlaza a la Directiva de `parallel` envolvente más cercana. Si se llama desde una parte de serie de un programa, o desde una región paralela anidada que se serializa, esta función devuelve 1.

Para obtener más información, vea [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Referencias cruzadas

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads función)

La función `omp_get_max_threads` devuelve un entero que se garantiza que sea al menos tan grande como el número de subprocesos que se utilizarían para formar un equipo si una región paralela sin una cláusula `num_threads` se vería en ese punto del código. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Lo siguiente expresa un límite inferior en el valor de `omp_get_max_threads`:

> *threads-Used-for-Next-team* <= `omp_get_max_threads`

Tenga en cuenta que si otra región paralela usa la cláusula `num_threads` para solicitar un número específico de subprocesos, la garantía en el límite inferior del resultado de `omp_get_max_threads` ya no se mantiene.

El valor devuelto de la función `omp_get_max_threads` se puede usar para asignar dinámicamente el almacenamiento suficiente para todos los subprocesos del equipo formado en la siguiente región paralela.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num función)

La función `omp_get_thread_num` devuelve el número de subprocesos, dentro de su equipo, del subproceso que ejecuta la función. El número de subprocesos está comprendido entre 0 y `omp_get_num_threads()`-1, ambos incluidos. El subproceso principal del equipo es el subproceso 0.

El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Si se llama desde una región serie, `omp_get_thread_num` devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function) función)

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs función)

La función `omp_get_num_procs` devuelve el número de procesadores que están disponibles para el programa en el momento en que se llama a la función. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel función)

La función `omp_in_parallel` devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela que se ejecuta en paralelo; de lo contrario, devuelve 0. El formato es como sigue:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecuta en paralelo, incluidas las regiones anidadas que se serializan.

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic función)

La función `omp_set_dynamic` habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de regiones paralelas. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* se evalúa como un valor distinto de cero, el entorno de tiempo de ejecución puede ajustar automáticamente el número de subprocesos que se usan para ejecutar futuras regiones paralelas para usar mejor los recursos del sistema. Como consecuencia, el número de subprocesos especificados por el usuario es el recuento máximo de subprocesos. El número de subprocesos del equipo que ejecutan una región paralela permanece fijo durante la duración de esa región paralela y lo detecta la función `omp_get_num_threads`.

Si *dynamic_threads* se evalúa como 0, se deshabilita el ajuste dinámico.

Esta función tiene los efectos descritos anteriormente cuando se llama desde una parte del programa en la que la función `omp_in_parallel` devuelve cero. Si se llama desde una parte del programa en la que la función `omp_in_parallel` devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Una llamada a `omp_set_dynamic` tiene prioridad sobre la variable de entorno `OMP_DYNAMIC`.

El valor predeterminado para el ajuste dinámico de los subprocesos está definido por la implementación. Como resultado, los códigos de usuario que dependen de un número específico de subprocesos para la ejecución correcta deben deshabilitar explícitamente los subprocesos dinámicos. No se necesitan implementaciones para proporcionar la capacidad de ajustar dinámicamente el número de subprocesos, pero es necesario proporcionar la interfaz para admitir la portabilidad en todas las plataformas.

#### <a name="microsoft-specific"></a>Específico de Microsoft

La compatibilidad actual de `omp_get_dynamic` y `omp_set_dynamic` es la siguiente:

El parámetro de entrada para `omp_set_dynamic` no afecta a la Directiva de subprocesos y no cambia el número de subprocesos. `omp_get_num_threads` siempre devuelve el número definido por el usuario, si está establecido, o el número de subproceso predeterminado. En la implementación actual de Microsoft, `omp_set_dynamic(0)` desactiva el subprocesamiento dinámico para que el conjunto de subprocesos existente se pueda reutilizar para la siguiente región paralela. `omp_set_dynamic(1)` activa el subprocesamiento dinámico descartando el conjunto de subprocesos existente y creando un nuevo conjunto para la próxima región paralela. El número de subprocesos del nuevo conjunto es el mismo que el conjunto anterior y se basa en el valor devuelto de `omp_get_num_threads`. Por lo tanto, para obtener el mejor rendimiento, utilice `omp_set_dynamic(0)` para reutilizar los subprocesos existentes.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic función)

La función `omp_get_dynamic` devuelve un valor distinto de cero si está habilitado el ajuste dinámico de los subprocesos y devuelve 0 en caso contrario. El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Si la implementación no implementa el ajuste dinámico del número de subprocesos, esta función siempre devuelve 0. Para obtener más información, vea [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Referencias cruzadas

- Para obtener una descripción del ajuste de subproceso dinámico, consulte [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested función)

La función `omp_set_nested` habilita o deshabilita el paralelismo anidado. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Si *Nested* se evalúa como 0, el paralelismo anidado está deshabilitado, que es el valor predeterminado, y el subproceso actual serializa y ejecuta las regiones paralelas anidadas. De lo contrario, el paralelismo anidado está habilitado y las regiones paralelas que están anidadas pueden implementar subprocesos adicionales para formar equipos anidados.

Esta función tiene los efectos descritos anteriormente cuando se llama desde una parte del programa en la que la función `omp_in_parallel` devuelve cero. Si se llama desde una parte del programa en la que la función `omp_in_parallel` devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene prioridad sobre la variable de entorno `OMP_NESTED`.

Cuando el paralelismo anidado está habilitado, el número de subprocesos utilizados para ejecutar regiones paralelas anidadas está definido por la implementación. Como resultado, las implementaciones compatibles con OpenMP pueden serializar regiones paralelas anidadas incluso cuando el paralelismo anidado está habilitado.

#### <a name="cross-references"></a>Referencias cruzadas

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested función)

La función `omp_get_nested` devuelve un valor distinto de cero si el paralelismo anidado está habilitado y 0 si está deshabilitado. Para obtener más información sobre el paralelismo anidado, consulte [omp_set_nested](#319-omp_set_nested-function). El formato es como sigue:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Si una implementación no implementa el paralelismo anidado, esta función siempre devuelve 0.

## <a name="32-lock-functions"></a>3,2 funciones de bloqueo

Las funciones descritas en esta sección manipulan los bloqueos que se usan para la sincronización.

En el caso de las siguientes funciones, la variable Lock debe tener el tipo `omp_lock_t`. Solo se debe tener acceso a esta variable a través de estas funciones. Todas las funciones de bloqueo requieren un argumento que tenga un puntero a `omp_lock_t` tipo.

- La función [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) Inicializa un bloqueo simple.
- La función [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) quita un bloqueo simple.
- La función [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) espera hasta que haya un bloqueo simple disponible.
- La función [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libera un bloqueo simple.
- La función [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) comprueba un bloqueo simple.

En el caso de las siguientes funciones, la variable Lock debe tener el tipo `omp_nest_lock_t`.  Solo se debe tener acceso a esta variable a través de estas funciones. Todas las funciones de bloqueo anidables requieren un argumento que tenga un puntero a `omp_nest_lock_t` tipo.

- La función [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) Inicializa un bloqueo anidable.
- La función [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) quita un bloqueo anidable.
- La función [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) espera hasta que haya un bloqueo anidable disponible.
- La función [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libera un bloqueo anidable.
- La función [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) prueba un bloqueo anidable.

Las funciones de bloqueo de OpenMP tienen acceso a la variable de bloqueo de tal forma que siempre leen y actualizan el valor más actual de la variable Lock. Por lo tanto, no es necesario que un programa de OpenMP incluya directivas de `flush` explícitas para asegurarse de que el valor de la variable de bloqueo es coherente entre los distintos subprocesos. (Puede que se necesiten directivas de `flush` para que los valores de otras variables sean coherentes).

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock y omp_init_nest_lock funciones

Estas funciones proporcionan el único medio para inicializar un bloqueo. Cada función inicializa el bloqueo asociado al *bloqueo* de parámetro para su uso en las próximas llamadas. El formato es como sigue:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

El estado inicial es desbloqueado (es decir, ningún subproceso posee el bloqueo). Para un bloqueo anidable, el recuento inicial de anidamiento es cero. No es compatible con la llamada a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 funciones de omp_destroy_lock y omp_destroy_nest_lock

Estas funciones garantizan que no se inicialice el *bloqueo* de la variable de bloqueo que señala. El formato es como sigue:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

No es compatible con la llamada a cualquiera de estas rutinas con una variable de bloqueo que no se haya inicializado o desbloqueado.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock y funciones de omp_set_nest_lock

Cada una de estas funciones bloquea el subproceso que ejecuta la función hasta que el bloqueo especificado esté disponible y, a continuación, establece el bloqueo. Un bloqueo simple está disponible si está desbloqueado. Un bloqueo anidable está disponible si está desbloqueado o si ya es propiedad del subproceso que ejecuta la función. El formato es como sigue:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Para un bloqueo simple, el argumento de la función `omp_set_lock` debe apuntar a una variable de bloqueo inicializada. La propiedad del bloqueo se concede al subproceso que ejecuta la función.

Para un bloqueo anidable, el argumento de la función `omp_set_nest_lock` debe apuntar a una variable de bloqueo inicializada. El recuento de anidamiento se incrementa y el subproceso se concede o mantiene la propiedad del bloqueo.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>las funciones de omp_unset_lock y omp_unset_nest_lock de 3.2.4

Estas funciones proporcionan el medio para liberar la propiedad de un bloqueo. El formato es como sigue:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

El argumento de cada una de estas funciones debe apuntar a una variable de bloqueo inicializada propiedad del subproceso que ejecuta la función. El comportamiento es indefinido si el subproceso no es el propietario del bloqueo.

Para un bloqueo simple, la función `omp_unset_lock` libera el subproceso que ejecuta la función desde la propiedad del bloqueo.

En el caso de un bloqueo anidable, la función `omp_unset_nest_lock` reduce el recuento de anidamiento y libera el subproceso que ejecuta la función de la propiedad del bloqueo si el recuento resultante es cero.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock y omp_test_nest_lock funciones

Estas funciones intentan establecer un bloqueo pero no bloquean la ejecución del subproceso. El formato es como sigue:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

El argumento debe apuntar a una variable de bloqueo inicializada. Estas funciones intentan establecer un bloqueo de la misma manera que `omp_set_lock` y `omp_set_nest_lock`, salvo que no bloquean la ejecución del subproceso.

Para un bloqueo simple, la función `omp_test_lock` devuelve un valor distinto de cero si el bloqueo se ha establecido correctamente; de lo contrario, devuelve cero.

En el caso de un bloqueo anidable, la función `omp_test_nest_lock` devuelve el nuevo recuento de anidamiento si el bloqueo se ha establecido correctamente. de lo contrario, devuelve cero.

## <a name="33-timing-routines"></a>3,3 rutinas de tiempo

Las funciones descritas en esta sección admiten un temporizador de reloj portátil:

- La función [omp_get_wtime](#331-omp_get_wtime-function) devuelve el tiempo de reloj transcurrido.
- La función [omp_get_wtick](#332-omp_get_wtick-function) devuelve segundos entre TICs de reloj sucesivos.

### <a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime función)

La función `omp_get_wtime` devuelve un valor de punto flotante de precisión doble igual al tiempo de reloj de la pared transcurrido en segundos desde algún momento en el pasado.  La "hora real" en el pasado es arbitraria, pero se garantiza que no cambia durante la ejecución del programa de la aplicación. El formato es como sigue:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Se prevé que la función se usará para medir los tiempos transcurridos tal y como se muestra en el ejemplo siguiente:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Los tiempos devueltos son "veces por subproceso", por lo que no es necesario que sean coherentes globalmente en todos los subprocesos que participan en una aplicación.

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick función)

La función `omp_get_wtick` devuelve un valor de punto flotante de precisión doble igual al número de segundos entre los ciclos de reloj sucesivos. El formato es como sigue:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
