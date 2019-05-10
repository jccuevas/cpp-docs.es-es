---
title: 3. Funciones de biblioteca en tiempo de ejecución
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 3eb6dc4110145a6c45dbdd772deaee3023e68e9d
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525045"
---
# <a name="3-run-time-library-functions"></a>3. Funciones de biblioteca en tiempo de ejecución

Esta sección describen las funciones de biblioteca en tiempo de ejecución de OpenMP C y C++. El encabezado  **\<omp.h >** declara dos tipos, varias funciones que pueden usarse para controlar y consultar el entorno de ejecución en paralelo y bloquear las funciones que pueden utilizarse para sincronizar el acceso a datos.

El tipo `omp_lock_t` es un tipo de objeto puede representar que un bloqueo está disponible o que un subproceso posee un bloqueo. Estos bloqueos se conocen como *bloqueos simples*.

El tipo `omp_nest_lock_t` es un tipo de objeto puede representar que un bloqueo está disponible o la identidad del subproceso que posee el bloqueo y un *anidar recuento* (descrito a continuación). Estos bloqueos se conocen como *bloqueos anidables*.

Las funciones de biblioteca son funciones externas con vinculación de "C".

Las descripciones en este capítulo se dividen en los temas siguientes:

- [Funciones de entorno de ejecución](#31-execution-environment-functions)
- [Funciones de bloqueo](#32-lock-functions)
- [Rutinas de control de tiempo](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 funciones de entorno de ejecución

Las funciones descritas en esta sección afectan y supervisión el entorno en paralelo, subprocesos y procesadores:

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads () (función)

El `omp_set_num_threads` función establece el número predeterminado de subprocesos que se utilizarán más adelante las regiones paralelas que no especifican un `num_threads` cláusula. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

El valor del parámetro *num_threads* debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para un conjunto completo de reglas sobre la interacción entre el `omp_set_num_threads` función y realizar un ajuste dinámico de subprocesos, vea [sección 2.3](2-directives.md#23-parallel-construct).

Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde el `omp_in_parallel` función devuelve cero. Si se llama desde una parte del programa donde el `omp_in_parallel` función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene prioridad sobre la `OMP_NUM_THREADS` variable de entorno. El valor predeterminado para el número de subprocesos, lo que se pueden establecer mediante una llamada a `omp_set_num_threads` o estableciendo la `OMP_NUM_THREADS` variable de entorno, se pueden reemplazar explícitamente en una sola `parallel` directiva especificando el `num_threads` cláusula.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_set_dynamic](#317-omp_set_dynamic-function) function
- [omp_get_dynamic](#318-omp_get_dynamic-function) function
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable de entorno
- [num_threads](2-directives.md#23-parallel-construct) cláusula

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads () (función)

El `omp_get_num_threads` función devuelve el número de subprocesos actualmente en el equipo de ejecución de la región paralela desde el que se llama. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

El `num_threads` cláusula, el `omp_set_num_threads` función y el `OMP_NUM_THREADS` variable de entorno controlar el número de subprocesos en un equipo.

Si el número de subprocesos no se ha establecido explícitamente por el usuario, el valor predeterminado es definido por la implementación. Esta función se enlaza a la envolvente más cercana `parallel` directiva. Si se llama desde una parte de la serie de un programa, o desde una región paralela anidada que se serializa, esta función devuelve 1.

#### <a name="cross-references"></a>Referencias cruzadas

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads () (función)

El `omp_get_max_threads` función devuelve un entero que se garantiza que al menos tan grande como el número de subprocesos que se usaría para formar un equipo si una región paralela sin un `num_threads` cláusula fuera a verse en ese momento en el código. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

La siguiente expresa un límite inferior del valor de `omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

Tenga en cuenta que si otro paralelo región utiliza el `num_threads` cláusula para solicitar un número específico de subprocesos, la garantía en el límite inferior del resultado de `omp_get_max_threads` no contiene mucho.

El `omp_get_max_threads` valor devuelto de la función puede utilizarse para asignar dinámicamente suficiente espacio de almacenamiento para todos los subprocesos en el equipo tiene el formato en la siguiente región paralela.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num () (función)

El `omp_get_thread_num` función devuelve el número de subprocesos dentro de su equipo, del subproceso que ejecuta la función. Los archivos de número de subproceso entre 0 y `omp_get_num_threads()`-1, ambos inclusive. El subproceso principal del equipo es 0.

El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Si se llama desde una región de la serie, `omp_get_thread_num` devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads ()](#312-omp_get_num_threads-function) (función)

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs () (función)

El `omp_get_num_procs` función devuelve el número de procesadores que están disponibles para el programa en el momento en que se llama a la función. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel () (función)

El `omp_in_parallel` función devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela que se ejecutan en paralelo; en caso contrario, devuelve 0. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecutan en paralelo, incluidas las regiones anidadas que se serializan.

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic () (función)

El `omp_set_dynamic` función habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de las regiones en paralelo. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* se evalúa como un valor distinto de cero, se puede ajustar el número de subprocesos que se utilizan para ejecutar próximas regiones en paralelo automáticamente por el entorno de tiempo de ejecución son los mejores usos de los recursos del sistema. Como consecuencia, el número de subprocesos especificados por el usuario es el número máximo de subprocesos. El número de subprocesos en el equipo de ejecución de una región paralela permanece fijo durante la duración de esa región paralela y notifica el `omp_get_num_threads` función.

Si *dynamic_threads* se evalúa como 0, se deshabilita el ajuste dinámico.

Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde el `omp_in_parallel` función devuelve cero. Si se llama desde una parte del programa donde el `omp_in_parallel` función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Una llamada a `omp_set_dynamic` tiene prioridad sobre la `OMP_DYNAMIC` variable de entorno.

El valor predeterminado para el ajuste dinámico de subprocesos es definido por la implementación. Como resultado, los códigos de usuario que dependen de un número específico de subprocesos para su ejecución correcta, deben deshabilitarse subprocesos dinámicos. Las implementaciones no son necesarias para proporcionar la capacidad de ajustar dinámicamente el número de subprocesos, pero son necesarios para proporcionar la interfaz para admitir la portabilidad entre todas las plataformas.

#### <a name="cross-references"></a>Referencias cruzadas

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic () (función)

El `omp_get_dynamic` función devuelve un valor distinto de cero si realizar un ajuste dinámico de subprocesos está habilitado y lo contrario, devuelve 0. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Si la implementación no implementa el ajuste dinámico del número de subprocesos, esta función siempre devuelve 0.

#### <a name="cross-references"></a>Referencias cruzadas

- Para obtener una descripción de ajuste dinámico del subproceso, vea [omp_set_dynamic ()](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested () (función)

El `omp_set_nested` función habilita o deshabilita el paralelismo anidado. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Si *anidada* se evalúa como 0, anidados paralelismo está deshabilitado, el valor predeterminado y las regiones paralelas anidadas se serializan y ejecutadas por el subproceso actual. En caso contrario, está habilitado paralelismo anidado y regiones en paralelo que están anidadas pueden implementar subprocesos adicionales para formar equipos anidados.

Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde el `omp_in_parallel` función devuelve cero. Si se llama desde una parte del programa donde el `omp_in_parallel` función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene prioridad sobre la `OMP_NESTED` variable de entorno.

Cuando se habilita el paralelismo anidado, el número de subprocesos usados para ejecutar regiones anidadas en paralelo es definido por la implementación. Como resultado, se permiten implementaciones compatibles con OpenMP para serializar regiones anidadas en paralelo incluso cuando se habilita el paralelismo anidado.

#### <a name="cross-references"></a>Referencias cruzadas

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested () (función)

El `omp_get_nested` función devuelve un valor distinto de cero si se habilita el paralelismo anidado y 0 si no lo está. Para obtener más información sobre el paralelismo anidado, vea [omp_set_nested ()](#319-omp_set_nested-function). El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Si una implementación no implementa el paralelismo anidado, esta función siempre devuelve 0.

## <a name="32-lock-functions"></a>3.2 funciones de bloqueo

Las funciones descritas en esta sección manipulan los bloqueos que se usa para la sincronización.

Para las siguientes funciones, la variable de bloqueo debe tener tipo `omp_lock_t`. Esta variable solo debe obtenerse a través de estas funciones. Todas las funciones de bloqueo requieren un argumento que tiene un puntero a `omp_lock_t` tipo.

- El [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) función inicializa un bloqueo simple.
- El [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) función quita un bloqueo simple.
- El [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) función espera hasta que esté disponible un bloqueo simple.
- El [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) función libera un bloqueo simple.
- El [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) función comprueba un bloqueo simple.

Para las siguientes funciones, la variable de bloqueo debe tener tipo `omp_nest_lock_t`.  Esta variable solo debe obtenerse a través de estas funciones. Todas las funciones de bloqueo anidable requieren un argumento que tiene un puntero a `omp_nest_lock_t` tipo.

- El [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) función inicializa un bloqueo anidable.
- El [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) función quita un bloqueo anidable.
- El [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) función espera hasta que un bloqueo anidable está disponible.
- El [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) función libera un bloqueo anidable.
- El [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) función comprueba un bloqueo anidable.

Las funciones de bloqueo de OpenMP tener acceso a la variable de bloqueo de manera que siempre lea y actualice el valor más reciente de la variable de bloqueo. Por lo tanto, no es necesario que un programa OpenMP para incluir explícita `flush` directivas para asegurarse de que el valor de la variable de bloqueo es coherente entre diferentes subprocesos. (Es posible que sea necesario para `flush` directivas para que los valores de otras variables sean coherentes.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock y omp_init_nest_lock funciones

Estas funciones proporcionan el único medio de inicializar un bloqueo. Cada función inicializa el bloqueo asociado al parámetro *bloqueo* para su uso en las llamadas futuras. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Se desbloquea el estado inicial (es decir, no hay ningún subproceso posee el bloqueo). Un bloqueo anidable, el recuento inicial de anidamiento es cero. No es conforme al llamar a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock y omp_destroy_nest_lock funciones

Estas funciones, asegúrese de que el apunta al bloquear la variable *bloqueo* no está inicializada. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Es no conforme para llamar a cualquiera de estas rutinas con una variable de bloqueo que ha sin inicializar o desbloqueado.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock y omp_set_nest_lock funciones

Cada una de estas funciones bloquea el subproceso que ejecuta la función hasta que el bloqueo especificado está disponible y, a continuación, Establece el bloqueo. Un bloqueo simple está disponible si está desbloqueada. Un bloqueo anidable está disponible si está desbloqueado o si ya tiene propietario por el subproceso que ejecuta la función. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Un bloqueo simple, el argumento para el `omp_set_lock` función debe apuntar a una variable inicializada de bloqueo. La propiedad del bloqueo se concede al subproceso de ejecución de la función.

Un bloqueo anidable, el argumento para el `omp_set_nest_lock` función debe apuntar a una variable inicializada de bloqueo. Se incrementa el recuento de anidamiento, y el subproceso se concede o conserva la propiedad del bloqueo.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock y omp_unset_nest_lock funciones

Estas funciones proporcionan los medios de liberar la propiedad de un bloqueo. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

El argumento para cada una de estas funciones debe apuntar a una variable inicializada de bloqueo que pertenece al subproceso de ejecución de la función. El comportamiento es indefinido si el subproceso no pertenece ese bloqueo.

Para obtener un bloqueo simple, el `omp_unset_lock` función libera el subproceso que ejecuta la función de la propiedad del bloqueo.

Para obtener un bloqueo anidable, el `omp_unset_nest_lock` función disminuye el recuento de anidamiento y las versiones el subproceso que ejecuta la función de la propiedad del bloqueo, si el recuento resultante es cero.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock y omp_test_nest_lock funciones

Estas funciones intentan establecer un bloqueo, pero no bloquean la ejecución del subproceso. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

El argumento debe apuntar a una variable inicializada de bloqueo. Estas funciones intentan establecer un bloqueo en la misma manera que `omp_set_lock` y `omp_set_nest_lock`, salvo que no impiden la ejecución del subproceso.

Para obtener un bloqueo simple, el `omp_test_lock` función devuelve un valor distinto de cero si el bloqueo se ha establecido correctamente; en caso contrario, devuelve cero.

Para obtener un bloqueo anidable, el `omp_test_nest_lock` función devuelve el nuevo recuento de anidamiento, si se estableció correctamente el bloqueo; en caso contrario, devuelve cero.

## <a name="33-timing-routines"></a>3.3 rutinas temporales

Las funciones descritas en esta sección admiten un temporizador del reloj portátil:

- El [omp_get_wtime ()](#331-omp_get_wtime-function) función devuelve el tiempo de reloj transcurrido.
- El [omp_get_wtick ()](#332-omp_get_wtick-function) función devuelve los segundos entre ciclos de reloj sucesivos.

### <a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime () (función)

El `omp_get_wtime` función devuelve un valor de punto flotante de precisión doble igual que el tiempo de reloj transcurrido en segundos desde alguna "hora del pasado".  El "tiempo real en el pasado" es arbitrario, pero garantiza que no cambian durante la ejecución de la aplicación. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Se prevé que se utilizará la función para medir los tiempos transcurridos tal como se muestra en el ejemplo siguiente:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Los tiempos de devueltos son "veces por subproceso" por lo que supone que no es necesario que sea globalmente coherente entre todos los subprocesos que participan en una aplicación.

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick () (función)

El `omp_get_wtick` función devuelve un valor de punto flotante de doble precisión igual al número de segundos entre ciclos de reloj sucesivos. El formato es como se detalla a continuación:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
