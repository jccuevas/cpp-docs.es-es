---
title: 2.4.1 for (construcción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac142c628f3c2bef0bc29a2ffd50df8a9efda400
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216542"
---
# <a name="241-for-construct"></a>2.4.1 for (Construcción)

El **para** directiva identifica una construcción de uso compartido de trabajo iterativa que especifica que las iteraciones del bucle asociada se ejecutarán en paralelo. Las iteraciones de la **para** bucle se distribuyen entre los subprocesos que ya existen en el equipo que ejecuta la construcción paralela a la que se enlaza. La sintaxis de la **para** construcción es como sigue:

```
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La cláusula es uno de los siguientes:

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate(** *variable-list* **)**

**reducción (** *operador* **:** *lista de variables* **)**

**Ordenada**

**programación (** *tipo* [**,** *chunk_size*] **)**

**nowait**

El **para** directiva impone restricciones en la estructura de los correspondientes **para** bucle. En concreto, la correspondiente **para** bucle debe tener la forma canónica:

**para (** *init-expr* **;** *var lógico op b*; *incr expr* **)**

*Init-expr*<br/>
Uno de los siguientes:

*var* = *lb*

*tipo entero var* = *lb*

*incr expr*<br/>
Uno de los siguientes:

++ *var*

*var* ++

-- *var*

*var* --

*var* += *incr*

*var* -= *incr*

*var* = *var* + *incr*

*var* = *incr* + *var*

*var* = *var* - *incr*

*var*<br/>
Una variable de entero con signo. Si esta variable se pueden compartir en caso contrario, se implícitamente hace privada para el tiempo que dure la **para**.   No se debe modificar esta variable dentro del cuerpo de la **para** instrucción. A menos que se especifica la variable **lastprivate**, su valor después de que el bucle es indeterminado.

*operación lógica*<br/>
Uno de los siguientes:

<

\<=

>

\>=

*lb*, *b*, y *incr*<br>
Las expresiones de enteros invariable de bucle. No hay ninguna sincronización durante la evaluación de estas expresiones. Por lo tanto, los efectos secundarios evaluados producir resultados indeterminados.

Tenga en cuenta que la forma canónica permite que el número de iteraciones del bucle debe calcularse en la entrada para el bucle. Este cálculo se realiza con los valores en el tipo de *var*, después de promociones de enteros. En particular, si el valor de *b* - *lb* + *incr* no se puede representar en que el tipo, el resultado es indeterminado. Además, si *lógico op* es < o \<= entonces *incr expr* debe hacer que *var* para aumentar en cada iteración del bucle.   Si *lógico op* es > o > =, a continuación, *incr expr* debe provocar *var* a disminuir en cada iteración del bucle.

El **programación** cláusula especifica cómo las iteraciones de la **para** bucle se dividen entre los subprocesos del equipo. La corrección de un programa no debe depender de qué subproceso ejecuta una iteración determinada. El valor de *chunk_size*, si se especifica, debe ser una expresión de entero invariable de bucle con un valor positivo. No hay ninguna sincronización durante la evaluación de esta expresión. Por lo tanto, los efectos secundarios evaluados producir resultados indeterminados. La programación *tipo* puede ser uno de los siguientes:

TABLA 2-1 **programación** cláusula *tipo* valores

|||
|-|-|
|estático|Cuando **programación (estático,** *chunk_size* **)** se especifica, las iteraciones se dividen en fragmentos de un tamaño especificado por *chunk_size*. Los fragmentos se asignan estáticamente a subprocesos en el equipo en un modo round-robin en el orden el número de subprocesos. Cuando no hay ninguna *chunk_size* se especifica, el espacio de la iteración se divide en fragmentos que son aproximadamente iguales en tamaño, con un solo fragmento asignado a cada subproceso.|
|dynamic|Cuando **programación (dynamic,** *chunk_size* **)** se especifica, las iteraciones se dividen en una serie de fragmentos, cada uno con *chunk_size* iteraciones. Cada fragmento se asigna a un subproceso que está esperando una asignación. El subproceso ejecuta el fragmento de iteraciones y, a continuación, espera para su asignación siguiente, hasta que ningún fragmento permanecen para asignarse. Tenga en cuenta que el último fragmento que se asignará puede tener un menor número de iteraciones. Cuando no hay ninguna *chunk_size* se especifica, el valor predeterminado es 1.|
|guiada por perfiles|Cuando **programación (guiado,** *chunk_size* **)** se especifica, las iteraciones se asignan a subprocesos en fragmentos con disminuir el tamaño. Cuando un subproceso finaliza su fragmento asignado de iteraciones, se asigna dinámicamente otro fragmento, hasta que no queda ninguna. Para un *chunk_size* de 1, el tamaño de cada fragmento es aproximadamente el número de iteraciones sin asignar dividido por el número de subprocesos. Estos tamaños aproximadamente disminuyen exponencialmente en 1. Para un *chunk_size* con valor *k* mayor que 1, los tamaños de aproximadamente disminuir exponencialmente a *k*, salvo que el último fragmento puede tener menos de  *k* iteraciones. Cuando no hay ninguna *chunk_size* se especifica, el valor predeterminado es 1.|
|motor en tiempo de ejecución|Cuando **Schedule (Runtime)** se especifica, la decisión sobre la programación se retrasa hasta el tiempo de ejecución. La programación *tipo* y tamaño de los fragmentos se puede elegir en tiempo de ejecución estableciendo la variable de entorno **OMP_SCHEDULE**. Si no se establece esta variable de entorno, la programación resultante es definido por la implementación. Cuando **Schedule (Runtime)** se especifica, *chunk_size* no debe especificarse.|

En ausencia de definido explícitamente **programación** cláusula, el valor predeterminado **programación** define la implementación.

Un programa compatible con OpenMP no debe depender de un programa en particular para su ejecución correcta. Un programa no debe confiar en una programación *tipo* que se ajuste exactamente a la descripción proporcionada más arriba, porque es posible que las variaciones en las implementaciones de la misma programación *tipo* a través de diferentes compiladores. Las descripciones se pueden usar para seleccionar la programación que es adecuada para una situación en particular.

El **ordenados** cláusula debe estar presente cuando **ordenados** directivas enlazar a la **para** construir.

Hay una barrera implícita al final de un **para** construir a menos que un **nowait** se especifica la cláusula.

Restricciones para el **para** directiva son los siguientes:

-   El **para** bucle debe ser un bloque estructurado y, además, su ejecución no debe terminar con un **salto** instrucción.

-   Los valores del bucle controlan las expresiones de la **para** bucle asociado con un **para** directiva debe ser el mismo para todos los subprocesos en el equipo.

-   El **para** variable de iteración del bucle debe tener un tipo entero con signo.

-   Una sola **programación** cláusula puede aparecer en un **para** directiva.

-   Una sola **ordenados** cláusula puede aparecer en un **para** directiva.

-   Una sola **nowait** cláusula puede aparecer en un **para** directiva.

-   Es si no especificado o con qué frecuencia los efectos secundarios dentro de la *chunk_size*, *lb*, *b*, o *incr* las expresiones se encuentran.

-   El valor de la *chunk_size* expresión debe ser el mismo para todos los subprocesos en el equipo.

## <a name="cross-references"></a>Referencias cruzadas:

-   **privada**, **firstprivate**, **lastprivate**, y **reducción** cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.

-   **OMP_SCHEDULE** vea variable de entorno [sección 4.1](../../parallel/openmp/4-1-omp-schedule.md) en página 48.

-   **ordenar** construir, consulte [sección 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) en la página 22.

-   [Apéndice D](../../parallel/openmp/d-using-the-schedule-clause.md), página 93, proporciona más información sobre el uso de la cláusula schedule.