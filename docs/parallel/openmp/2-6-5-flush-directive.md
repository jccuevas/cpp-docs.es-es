---
title: 2.6.5 flush (directiva) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad3b34195015f57955c5be685807ec43f0a8f8c6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="265-flush-directive"></a>2.6.5 flush (Directiva)
El **vaciar** directiva, ya sea explícita o implícita, especifica un punto de secuencia "entre subprocesos" en el que debe asegurarse de que todos los subprocesos de un equipo tienen una vista coherente de ciertos objetos (especificadas a continuación) en la implementación memoria. Esto significa que las anteriores evaluaciones de expresiones que hacen referencia a esos objetos están completos y las evaluaciones subsiguientes no han comenzado aún. Por ejemplo, los compiladores deben restaurar los valores de los objetos de registros en la memoria y hardware que necesite vaciar los búferes de escritura en la memoria y volver a cargar los valores de los objetos de la memoria.  
  
 La sintaxis de la **vaciar** directiva es como sigue:  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 Si los objetos que requieren sincronización pueden designarse por las variables, esas variables se pueden especificar en la parte opcional *lista de variables*. Si un puntero se encuentra en la *lista de variables*, se vacía el propio puntero, no el objeto hace referencia el puntero.  
  
 A **vaciar** la directiva sin un *lista de variables* compartidos todos los objetos excepto objetos inaccesibles se sincroniza con una duración de almacenamiento automática. (Esto es probable que tenga más sobrecarga que un **vaciar** con un *lista de variables*.) A **vaciar** la directiva sin un *lista de variables* está implícito en las siguientes directivas:  
  
-   `barrier`  
  
-   En la entrada y la salida de **crítico**  
  
-   En la entrada y la salida de `ordered`  
  
-   En la entrada y la salida de **paralelas**  
  
-   Al salir de **para**  
  
-   Al salir de **secciones**  
  
-   Al salir de **único**  
  
-   En la entrada y la salida de **for paralelos**  
  
-   En la entrada y la salida de **secciones en paralelo**  
  
 La directiva se considera implícita si una `nowait` cláusula está presente. Se debe tener en cuenta que la **vaciar** directiva no está implícito para cualquiera de las siguientes acciones:  
  
-   Las entradas a **para**  
  
-   En la entrada o salida del **maestro**  
  
-   Las entradas para **secciones**  
  
-   Las entradas para **único**  
  
 Una referencia que tiene acceso al valor de un objeto con un tipo calificado como volátil se comporta como si hubiera un **vaciar** Directiva especifique ese objeto en el punto de secuencia anterior. Una referencia que modifica el valor de un objeto con un tipo calificado como volátil se comporta como si hubiera un **vaciar** Directiva especifique ese objeto en el momento de la secuencia.  
  
 Tenga en cuenta que, dado el **vaciar** directiva no tiene una instrucción del lenguaje C como parte de su sintaxis, hay algunas restricciones en su posición dentro de un programa. Vea [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) para la gramática formal. En el ejemplo siguiente se muestra estas restricciones.  
  
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
  
 Restricciones a la **vaciar** directiva son los siguientes:  
  
-   Una variable especificada en un **vaciar** directiva no debe tener un tipo de referencia.