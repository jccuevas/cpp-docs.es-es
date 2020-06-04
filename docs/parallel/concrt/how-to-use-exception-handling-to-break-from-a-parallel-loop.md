---
title: 'Cómo: Usar el control de excepciones para interrumpir un bucle Parallel'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: a5576e8f2416804cac89f5ec34005f4e08b99c47
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142113"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Cómo: Usar el control de excepciones para interrumpir un bucle Parallel

En este tema se muestra cómo escribir un algoritmo de búsqueda para una estructura de árbol básica.

La [cancelación](cancellation-in-the-ppl.md) del tema explica el rol de cancelación en la biblioteca de patrones de procesamiento paralelo. El uso del control de excepciones es una manera menos eficaz de cancelar el trabajo paralelo que el uso de los métodos [Concurrency:: task_group:: CANCEL](reference/task-group-class.md#cancel) y [concurrency:: structured_task_group:: CANCEL](reference/structured-task-group-class.md#cancel) . Sin embargo, un escenario en el que el uso del control de excepciones para cancelar el trabajo es adecuado es cuando se llama a una biblioteca de terceros que utiliza tareas o algoritmos paralelos pero no proporciona un objeto `task_group` o `structured_task_group` para cancelar.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo de `tree` básico que contiene un elemento de datos y una lista de nodos secundarios. En la sección siguiente se muestra el cuerpo del método `for_all`, que realiza de forma recursiva una función de trabajo en cada nodo secundario.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el método `for_all`. Usa el algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) para realizar una función de trabajo en cada nodo del árbol en paralelo.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra la función `search_for_value`, que busca un valor en el objeto `tree` proporcionado. Esta función pasa al método `for_all` una función de trabajo que produce cuando encuentra un nodo de árbol que contiene el valor proporcionado.

Supongamos que la clase `tree` la proporciona una biblioteca de terceros y que no se puede modificar. En este caso, el uso del control de excepciones es adecuado porque el método `for_all` no proporciona un objeto `task_group` o `structured_task_group` al llamador. Por lo tanto, la función de trabajo no puede cancelar directamente su grupo de tareas primario.

Cuando la función de trabajo que se proporciona a un grupo de tareas produce una excepción, el tiempo de ejecución detiene todas las tareas que se encuentran en el grupo de tareas (incluidos los grupos de tareas secundarios) y descarta cualquier tarea que no se haya iniciado todavía. La función `search_for_value` utiliza una `try`-bloque `catch` para capturar la excepción e imprimir el resultado en la consola.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un objeto `tree` y se busca en él varios valores en paralelo. La función `build_tree` se muestra más adelante en este tema.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

En este ejemplo se usa el algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) para buscar valores en paralelo. Para obtener más información acerca de este algoritmo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo completo se usa el control de excepciones para buscar valores en una estructura de árbol básica.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `task-tree-search.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Task-Tree-Search. cpp**

## <a name="see-also"></a>Consulte también

[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group (clase)](reference/task-group-class.md)<br/>
[structured_task_group (clase)](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each función)](reference/concurrency-namespace-functions.md#parallel_for_each)
