---
title: 'Cómo: utilizar excepciones para interrumpir un bucle Parallel | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a15910885b26c8026a6e504ef36d492cf63445e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379832"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Cómo: Usar el control de excepciones para interrumpir un bucle Parallel

En este tema se muestra cómo escribir un algoritmo de búsqueda para una estructura de árbol básica.

El tema [cancelación](cancellation-in-the-ppl.md) explica el rol de cancelación en la biblioteca de patrones de procesamiento paralelo. El uso del control de excepciones es una forma menos eficaz para cancelar el trabajo paralelo que el uso de la [task_group](reference/task-group-class.md#cancel) y [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) métodos. Sin embargo, un escenario donde es adecuado el uso del control de excepciones para cancelar el trabajo es al llamar a una biblioteca de terceros que usa las tareas o algoritmos paralelos, pero no proporciona un `task_group` o `structured_task_group` objeto que se va a cancelar.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un basic `tree` tipo que contiene un elemento de datos y una lista de nodos secundarios. En la sección siguiente se muestra el cuerpo de la `for_all` método, que de forma recurrente realiza una función de trabajo en cada nodo secundario.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra el `for_all` método. Usa el [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo para realizar una función de trabajo en cada nodo del árbol en paralelo.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra la función `search_for_value`, que busca un valor en el objeto `tree` proporcionado. Esta función se pasa a la `for_all` método es una función de trabajo que se produce cuando encuentra un nodo de árbol que contiene el valor proporcionado.

Suponga que el `tree` clase se proporciona una biblioteca de terceros y que no pueden modificarlo. En este caso, el uso del control de excepciones es adecuado porque el `for_all` método no proporciona un `task_group` o `structured_task_group` objeto al llamador. Por lo tanto, la función de trabajo no puede cancelar directamente de su grupo de tareas primario.

Cuando la función de trabajo que se proporciona a un grupo de tareas produce una excepción, el tiempo de ejecución detiene todas las tareas que se encuentran en el grupo de tareas (incluidos los grupos de tareas secundarios) y descarta cualquier tarea que todavía no se han iniciado. El `search_for_value` función usa un `try` - `catch` bloque para capturar la excepción e imprimir el resultado en la consola.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un `tree` de objetos y las búsquedas de varios valores en paralelo. El `build_tree` función se muestra más adelante en este tema.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

Este ejemplo se usa el [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo para buscar valores en paralelo. Para obtener más información acerca de este algoritmo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Ejemplo

El siguiente ejemplo completo usa control de excepciones para buscar valores en una estructura de árbol básica.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `task-tree-search.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe de tarea árbol/EHsc-search.cpp**

## <a name="see-also"></a>Vea también

[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group (clase)](reference/task-group-class.md)<br/>
[structured_task_group (clase)](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each (función)](reference/concurrency-namespace-functions.md#parallel_for_each)

