---
title: 2.4.1 for (construcción) | Documentos de Microsoft
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
ms.openlocfilehash: d5165c21f0bf6f2b9757550208d5e8e26a2bd3b1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693554"
---
# <a name="241-for-construct"></a>2.4.1 for (Construcción)
El **para** directiva identifica una construcción de uso compartido de trabajo iterativa que especifica que las iteraciones del bucle asociado se ejecutarán en paralelo. Las iteraciones de la **para** bucle se distribuyen entre varios subprocesos que ya existen en el equipo que ejecuta la construcción paralela a la que se enlaza. La sintaxis de la **para** construcción es como sigue:  
  
```  
#pragma omp for [clause[[,] clause] ... ] new-linefor-loop  
```  
  
 La cláusula es uno de los siguientes:  
  
 **private(** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **lastprivate(** *variable-list* **)**  
  
 **reducción (** *operador* **:** *variable-lista ***)**  
  
 **ordenada**  
  
 **programación (** *tipo*[, *chunk_size*]**)**  
  
 **nowait**  
  
 El **para** directiva impone restricciones en la estructura de los correspondientes **para** bucle. En concreto, la correspondiente **para** bucle debe tener la forma canónica:  
  
 **para (** *init-expr* **;** *var lógico op b*; *incr-expr ***)**  
  
 *Init-expr*  
 Uno de los siguientes:  
  
 *var* = *lb*  
  
 *tipo de entero var* = *lb*  
  
 *incr expr*  
 Uno de los siguientes:  
  
 ++*Var*  
  
 *var* ++  
  
 -- *Var*  
  
 *var* --  
  
 *var* += *incr*  
  
 *var* -= *incr*  
  
 *var* = *var* + *incr*  
  
 *var* = *incr* + *var*  
  
 *var* = *var* - *incr*  
  
 *var*  
 Una variable de entero con signo. Si esta variable se compartirá en caso contrario, se implícitamente hace privada para la duración de la **para**.   Esta variable no debe modificarse en el cuerpo de la **para** instrucción. A menos que se especifica la variable **lastprivate**, su valor después de que el bucle es indeterminado.  
  
 *lógica-op*  
 Uno de los siguientes:  
  
 <  
  
 \<=  
  
 >  
  
 \>=  
  
 *lb*, *b*, y *incr*  
 Bucle expresiones entero invariable. No hay ninguna sincronización durante la evaluación de estas expresiones. Por lo tanto, efectos secundarios evaluados generan resultados indeterminados.  
  
 Tenga en cuenta que la forma canónica permite que el número de iteraciones del bucle debe calcularse en la entrada para el bucle. Este cálculo se realiza sin los valores en el tipo de *var*, después de promociones de enteros. En particular, si el valor de *b* - *lb* + *incr* no se puede representar en que el tipo, el resultado es indeterminado. Además, si *lógico op* es < o \<=, a continuación, *incr expr* deben provocar *var* para aumentar en cada iteración del bucle.   Si *lógico op* es > o > =, a continuación, *incr expr* deben provocar *var* reducir en cada iteración del bucle.  
  
 El **programación** cláusula especifica cómo iteraciones de la **para** bucle se dividen entre los subprocesos del equipo. La corrección de un programa no debe depender de qué subproceso ejecuta una iteración concreta. El valor de *chunk_size*, si se especifica, debe ser una expresión de entero invariable de bucle con un valor positivo. No hay ninguna sincronización durante la evaluación de esta expresión. Por lo tanto, efectos secundarios evaluados generan resultados indeterminados. La programación *tipo* puede ser uno de los siguientes:  
  
 TABLA 2-1 **programación** cláusula *tipo* valores  
  
|||  
|-|-|  
|estático|Cuando **programación (estático,** *chunk_size ***)** se especifica, iteraciones se dividen en fragmentos de un tamaño especificado por *chunk_size*. Los fragmentos se asignaron estáticamente a subprocesos en el equipo en un modo round-robin en el orden del número de subprocesos. Si no *chunk_size* se especifica, el espacio de la iteración se divide en fragmentos que son aproximadamente iguales en tamaño, con un fragmento que se asigna a cada subproceso.|  
|dynamic|Cuando **programación (dinámicos,** *chunk_size ***)** se especifica, las iteraciones se dividen en una serie de fragmentos, cada uno con *chunk_size* iteraciones. Cada fragmento se asigna a un subproceso que está esperando una asignación. El subproceso ejecuta el fragmento de iteraciones y, a continuación, espera su asignación siguiente, hasta que no queden ningún fragmento al que se asignará. Tenga en cuenta que el último fragmento que se asignará puede tener un menor número de iteraciones. Si no *chunk_size* se especifica, el valor predeterminado es 1.|  
|guiadas por perfiles|Cuando **programación (interactiva,** *chunk_size ***)** se especifica, las iteraciones se asignan a los subprocesos en fragmentos con decrecientes tamaños. Cuando un subproceso finaliza su bloque asignado de iteraciones, se asigna dinámicamente otro fragmento, hasta que no queda ninguna. Para una *chunk_size* de 1, el tamaño de cada fragmento es aproximadamente igual al número de iteraciones sin asignar dividido por el número de subprocesos. Estos tamaños aproximadamente disminuyen exponencialmente en 1. Para una *chunk_size* con valor *k* mayor que 1, los tamaños de aproximadamente disminuir exponencialmente a *k*, excepto en que el último fragmento puede tener menos de  *k* iteraciones. Si no *chunk_size* se especifica, el valor predeterminado es 1.|  
|motor en tiempo de ejecución|Cuando **schedule(runtime)** se especifica, la decisión sobre la programación se retrasa hasta el tiempo de ejecución. La programación *tipo* y tamaño de los fragmentos se puede seleccionar en tiempo de ejecución estableciendo la variable de entorno **OMP_SCHEDULE**. Si no se establece esta variable de entorno, la programación resultante está definido por la implementación. Cuando **schedule(runtime)** se especifica, *chunk_size* no se debe especificar.|  
  
 En ausencia de definido explícitamente **programación** cláusula, el valor predeterminado **programación** define la implementación.  
  
 Un programa compatible con OpenMP no debe depender de una programación determinada para su ejecución correcta. Un programa no debe confiar en una programación *tipo* que se ajuste exactamente a la descripción dada anteriormente, porque es posible tener variaciones en las implementaciones de la misma programación *tipo* a través de compiladores diferentes. Las descripciones se pueden utilizar para seleccionar el plan que es adecuado para una situación determinada.  
  
 El **ordenados** cláusula debe estar presente cuando **ordenados** directivas enlazar a la **para** construir.  
  
 Hay una barrera implícita al final de un **para** construir a menos que un **nowait** se especifica la cláusula.  
  
 Restricciones a la **para** directiva son los siguientes:  
  
-   El **para** bucle debe ser un bloque estructurado y, además, su ejecución no debe terminar con un **salto** instrucción.  
  
-   Los valores del bucle controlan las expresiones de la **para** bucle asociado con un **para** directiva debe ser el mismo para todos los subprocesos en el equipo.  
  
-   El **para** variable de iteración del bucle debe tener un tipo de entero con signo.  
  
-   Solo una **programación** cláusula puede aparecer en un **para** directiva.  
  
-   Solo una **ordenados** cláusula puede aparecer en un **para** directiva.  
  
-   Solo una **nowait** cláusula puede aparecer en un **para** directiva.  
  
-   Es if no especificado o con qué frecuencia los efectos secundarios dentro de la *chunk_size*, *lb*, *b*, o *incr* aparecen expresiones.  
  
-   El valor de la *chunk_size* expresión debe ser el mismo para todos los subprocesos en el equipo.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **privada**, **firstprivate**, **lastprivate**, y **reducción** cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.  
  
-   **OMP_SCHEDULE** vea variable de entorno [sección 4.1](../../parallel/openmp/4-1-omp-schedule.md) en página 48.  
  
-   **ordenados** construir, consulte [sección 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) en página 22.  
  
-   [Apéndice D](../../parallel/openmp/d-using-the-schedule-clause.md), página 93, se proporciona más información sobre el uso de la cláusula schedule.