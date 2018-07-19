---
title: 'Cómo: utilizar excepciones para interrumpir un bucle paralelo | Documentos de Microsoft'
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
ms.openlocfilehash: 6bacb9ea6a451026f7a515878cb649090ed9cbf4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691851"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Cómo: Usar el control de excepciones para interrumpir un bucle Parallel
Este tema muestra cómo escribir un algoritmo de búsqueda para una estructura de árbol básica.  
  
 El tema [cancelación](cancellation-in-the-ppl.md) explica el rol de cancelación en la biblioteca de patrones de procesamiento paralelo. El uso del control de excepciones es una forma menos eficaz de cancelar el trabajo paralelo que el uso de la [concurrency::task_group::cancel](reference/task-group-class.md#cancel) y [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) métodos. Sin embargo, un escenario donde el uso del control de excepciones para cancelar el trabajo es adecuado es cuando se llama a una biblioteca de otro fabricante que usa tareas o algoritmos paralelos, pero no proporciona un `task_group` o `structured_task_group` objeto que se va a cancelar.  

  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un basic `tree` tipo que contiene un elemento de datos y una lista de nodos secundarios. La siguiente sección muestra el cuerpo de la `for_all` método, que de forma recurrente realiza una función de trabajo en cada nodo secundario.  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se muestra la `for_all` método. Usa el [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo para realizar una función de trabajo en cada nodo del árbol en paralelo.  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra la función `search_for_value`, que busca un valor en el objeto `tree` proporcionado. Esta función se pasa a la `for_all` método es una función de trabajo que se produce cuando encuentra un nodo de árbol que contiene el valor proporcionado.  
  
 Se asume que la `tree` clase se proporciona una biblioteca de terceros y que no es posible modificarla. En este caso, el uso del control de excepciones es adecuado porque la `for_all` método no proporciona un `task_group` o `structured_task_group` objeto al autor de llamada. Por lo tanto, la función de trabajo es no se puede cancelar directamente su grupo de tareas primario.  
  
 Cuando la función de trabajo que se proporciona a un grupo de tareas produce una excepción, el tiempo de ejecución detiene todas las tareas que se encuentran en el grupo de tareas (incluidos los grupos de tareas secundarios) y descarta cualquier tarea que no se ha iniciado todavía. El `search_for_value` función utiliza un `try` - `catch` bloque para capturar la excepción e imprimir el resultado en la consola.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un `tree` de objeto y busca varios valores en paralelo. El `build_tree` función se muestra más adelante en este tema.  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 Este ejemplo se utiliza la [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo para buscar valores en paralelo. Para obtener más información acerca de este algoritmo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
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
  
 **cl.exe/EHsc tarea-tree-search.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)   
 [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [task_group (clase)](reference/task-group-class.md)   
 [structured_task_group (clase)](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel_for_each (función)](reference/concurrency-namespace-functions.md#parallel_for_each)


