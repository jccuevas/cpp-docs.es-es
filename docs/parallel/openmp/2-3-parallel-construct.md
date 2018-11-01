---
title: 2.3 parallel (Construcción)
ms.date: 11/04/2016
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
ms.openlocfilehash: 6ee7539af05bef1fdca117d806900f2f5a9c0d7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494680"
---
# <a name="23-parallel-construct"></a>2.3 parallel (Construcción)

La directiva siguiente define una región paralela, que es una región del programa que se ejecuta en varios subprocesos en paralelo. Se trata de la construcción fundamental que se inicia la ejecución en paralelo.

```
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

El *cláusula* es uno de los siguientes:

**if(** *scalar-expression* **)**

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**default(shared &#124; none)**

**shared(** *variable-list* **)**

**copyin(** *variable-list* **)**

**reducción (** *operador* **:***lista de variables* **)**

**num_threads(** *integer-expression* **)**

Cuando un subproceso encuentra una construcción paralela, se crea un grupo de subprocesos si se cumple una de los casos siguientes:

- No **si** cláusula está presente.

- El **si** expresión se evalúa como un valor distinto de cero.

Este subproceso se convierte en el subproceso principal del equipo, con un número de subprocesos de 0, y todos los subprocesos en el equipo, incluido el subproceso principal, la región se ejecutan en paralelo. Si el valor de la **si** expresión es cero, se serializa la región.

Para determinar el número de subprocesos que se solicitan, se considerarán las reglas siguientes en orden. Se aplicará la primera regla cuya condición se cumple:

1. Si el **num_threads** cláusula está presente, el valor de la expresión de entero es el número de subprocesos que se solicita.

1. Si el **omp_set_num_threads ()** se ha llamado la función de biblioteca y, después, el valor del argumento en la llamada ha ejecutado más recientemente es el número de subprocesos que se solicita.

1. Si la variable de entorno **OMP_NUM_THREADS** está definido, el valor de esta variable de entorno es el número de subprocesos que se solicita.

1. Si se usa ninguno de los métodos anteriores, el número de subprocesos es definido por la implementación.

Si el **num_threads** cláusula está presente, a continuación, reemplaza el número de subprocesos solicitado por el **omp_set_num_threads ()** función de biblioteca o el **OMP_NUM_THREADS** se aplica a la variable de entorno solo para la región paralela. Regiones en paralelo posteriores no se ven afectadas por ella.

El número de subprocesos que se ejecutan en la región paralela también depende de si está habilitado el ajuste dinámico del número de subprocesos. Si se deshabilita el ajuste dinámico, el número solicitado de subprocesos ejecutará la región paralela. Si está habilitado el ajuste dinámico, a continuación, el número solicitado de subprocesos es el número máximo de subprocesos que se pueden ejecutar a la región paralela.

Si se encuentra una región paralela mientras está deshabilitado el ajuste dinámico del número de subprocesos y el número de subprocesos solicitado para la región paralela supera el número que puede proporcionar el sistema de tiempo de ejecución, el comportamiento del programa es definido por la implementación. Una implementación, por ejemplo, puede interrumpir la ejecución del programa, o puede serializar la región paralela.

El **omp_set_dynamic ()** función de biblioteca y el **OMP_DYNAMIC** variable de entorno puede utilizarse para habilitar y deshabilitar el ajuste dinámico del número de subprocesos.

El número de procesadores físicos hospedando en realidad los subprocesos en un momento dado es definido por la implementación. Una vez creado, el número de subprocesos en el equipo permanece constante para la duración de esa región paralela. Puede cambiarse explícitamente por el usuario o automáticamente por el sistema de tiempo de ejecución de una región paralela a otra.

Se ejecutan las instrucciones incluidas en la extensión de la región paralela dinámica por cada subproceso, y cada subproceso puede ejecutar una ruta de acceso de las instrucciones que es diferente de los demás subprocesos. Las directivas que se encuentra fuera de la extensión léxica de una región paralela se conocen como directivas huérfanas.

Hay una barrera implícita al final de una región paralela. Solo el subproceso principal del equipo continúa la ejecución al final de una región paralela.

Si un subproceso en un equipo que ejecuta una región paralela encuentra otra construcción paralela, crea un nuevo equipo y se convierte en el maestro de ese nuevo equipo. Las regiones paralelas anidadas se serializan de forma predeterminada. Como resultado, de forma predeterminada, una región paralela anidada se ejecuta por un equipo que se compone de un subproceso. Se puede cambiar el comportamiento predeterminado mediante el uso de la función de biblioteca de tiempo de ejecución **omp_set_nested ()** o la variable de entorno **OMP_NESTED**. Sin embargo, el número de subprocesos en un equipo que ejecute una región paralela anidada es definido por la implementación.

Restricciones para el **paralelo** directiva son los siguientes:

- A lo sumo uno **si** cláusula puede aparecer en la directiva.

- No se especifica si cualquiera de efectos dentro expresión o **num_threads** expresión se producen.

- Un **throw** ejecuta dentro de una región paralela debe provocar que la ejecución reanudar dentro de la extensión dinámica del mismo bloque estructurado y se debe detectar mediante el mismo subproceso que produjo la excepción.

- Una sola **num_threads** cláusula puede aparecer en la directiva. El **num_threads** expresión se evalúa fuera del contexto de la región paralela y se debe evaluar como un valor entero positivo.

- El orden de evaluación de la **si** y **num_threads** cláusulas no se ha especificado.

## <a name="cross-references"></a>Referencias cruzadas:

- **privada**, **firstprivate**, **predeterminada**, **compartido**, **copyin**, y **reducción**cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.

- **OMP_NUM_THREADS** variable de entorno, [4.2 sección](../../parallel/openmp/4-2-omp-num-threads.md) en página 48.

- **omp_set_dynamic ()** función de biblioteca, consulte [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.

- **OMP_DYNAMIC** vea variable de entorno [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.

- **omp_set_nested ()** de función, vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.

- **OMP_NESTED** vea variable de entorno [sección 4.4](../../parallel/openmp/4-4-omp-nested.md) en la página 49.

- **omp_set_num_threads ()** función de biblioteca, consulte [sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.