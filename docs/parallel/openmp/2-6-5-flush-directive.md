---
title: 2.6.5 flush (Directiva)
ms.date: 11/04/2016
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
ms.openlocfilehash: 7aca747a3d9645be4f9888b072127dc3040280fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660088"
---
# <a name="265-flush-directive"></a>2.6.5 flush (Directiva)

El **vaciar** directiva, ya sea explícita o implícita, especifica un punto de secuencia "entre subprocesos" en el que se requiere la implementación para asegurarse de que todos los subprocesos en un equipo tienen una vista coherente de ciertos objetos (especificadas a continuación) en memoria. Esto significa que finalizan las evaluaciones anteriores de las expresiones que hacen referencia a esos objetos y las evaluaciones posteriores todavía no ha comenzado. Por ejemplo, los compiladores deben restaurar los valores de los objetos de los registros a la memoria y hardware que deba vaciar los búferes de escritura a la memoria y volver a los valores de los objetos de la memoria.

La sintaxis de la **vaciar** directiva es como sigue:

```
#pragma omp flush [(variable-list)]  new-line
```

Si los objetos que requieren sincronización pueden designarse por variables y, después, esas variables se pueden especificar en el elemento opcional *variable lista*. Si un puntero se encuentra en la *lista de variables*, el propio puntero se vacía, no el objeto hace referencia el puntero.

Un **vaciar** la directiva sin un *variable lista* sincroniza los objetos compartidos todo excepto los objetos inaccesibles con una duración de almacenamiento automático. (Esto es probable que tenga más sobrecarga que una **vaciar** con un *lista de variables*.) Un **vaciar** la directiva sin un *variable lista* está implícito en las siguientes directivas:

- `barrier`

- En la entrada y la salida de **crítica**

- En la entrada y la salida de `ordered`

- En la entrada y la salida de **paralelo**

- Al salir de **para**

- Al salir de **secciones**

- Al salir de **único**

- En la entrada y la salida de **paralelas para**

- En la entrada y la salida de **secciones en paralelo**

La directiva no está implícita si un `nowait` cláusula está presente. Se debe tener en cuenta que el **vaciar** directiva no está implícito para cualquiera de las siguientes acciones:

- En la entrada a **para**

- En la entrada o salida de **maestro**

- En la entrada a **secciones**

- En la entrada a **único**

Una referencia que tiene acceso al valor de un objeto con un tipo calificado como volátil se comporta como si hubiera un **vaciar** Directiva especifique ese objeto en el momento de la secuencia anterior. Una referencia que modifica el valor de un objeto con un tipo calificado como volátil se comporta como si hubiera un **vaciar** Directiva especifique ese objeto en el momento de la secuencia.

Tenga en cuenta que dado que la **vaciar** directiva no tiene una instrucción del lenguaje C como parte de su sintaxis, hay algunas restricciones en su posición dentro de un programa. Consulte [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) para la gramática formal. El ejemplo siguiente muestra estas restricciones.

```
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Restricciones para el **vaciar** directiva son los siguientes:

- Una variable especificada en un **vaciar** directiva no debe tener un tipo de referencia.