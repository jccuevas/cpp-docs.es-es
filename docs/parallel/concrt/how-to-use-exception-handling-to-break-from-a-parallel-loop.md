---
title: "C&#243;mo: Usar el control de excepciones para interrumpir un bucle Parallel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "algoritmo de búsqueda, escribir [Runtime de simultaneidad]"
  - "escribir un algoritmo de búsqueda [Runtime de simultaneidad]"
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Usar el control de excepciones para interrumpir un bucle Parallel
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo escribir un algoritmo de búsqueda para una estructura de árbol básica.  
  
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md) explica el rol de cancelación en la Biblioteca de modelos de procesamiento paralelo \(PPL\).  El uso del control de excepciones es una manera menos eficaz de cancelar el trabajo paralelo que el uso de los métodos de [concurrency::task\_group::cancel](../Topic/task_group::cancel%20Method.md) y de [concurrency::structured\_task\_group::cancel](../Topic/structured_task_group::cancel%20Method.md) .  Sin embargo, un escenario donde es apropiado el uso del control de excepciones para cancelar trabajo es cuando se llama a una biblioteca de terceros que use tareas o algoritmos paralelos pero no proporcione un objeto `task_group` o `structured_task_group` para la cancelación.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra un tipo `tree` básico que contiene un elemento de datos y una lista de nodos secundarios.  En la siguiente sección se muestra el cuerpo del método `for_all`, que realiza una función de trabajo en cada nodo secundario de forma recursiva.  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el método `for_all`.  Usa el algoritmo de [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) para realizar una función de trabajo en cada nodo del árbol en paralelo.  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se muestra la función `search_for_value`, que busca un valor en el objeto `tree` proporcionado.  Esta función pasa al método `for_all` una función de trabajo que se inicia cuando encuentra un nodo de árbol que contiene el valor proporcionado.  
  
 Suponga que la clase `tree` está proporcionada por una biblioteca de terceros y que no puede modificarla.  En este caso, el uso del control de excepciones es adecuado porque el método `for_all` no proporciona un objeto `task_group` o `structured_task_group` al llamador.  Por consiguiente, la función de trabajo no puede cancelar su grupo de tareas primario directamente.  
  
 Cuando la función de trabajo que se proporciona a un grupo de tareas produce una excepción, el runtime detiene todas las tareas incluidas en el grupo de tareas \(y cualquier grupo de tareas secundario\) y descarta cualquier tarea que no se haya iniciado todavía.  La función `search_for_value` usa un bloque `try`\-`catch` para capturar la excepción e imprimir el resultado en la consola.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se crea un objeto `tree` y se buscan en él varios valores en paralelo.  La función `build_tree` se muestra más adelante en este tema.  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 Este ejemplo utiliza el algoritmo de [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) para buscar valores en paralelo.  Para obtener más información sobre este algoritmo, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## Ejemplo  
 En el siguiente ejemplo completo se usa el control de excepciones para buscar valores en una estructura de árbol básica.  
  
 [!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/CPP/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo.  
  
  **Encontrar un nodo con el valor 32614.**  
**Encontrar un nodo con el valor 86131.**  
**No encontró nodo con el valor 17522.**   
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio, o péguelo en un archivo denominado `task-tree-search.cpp` y después se ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc task\-tree\-search.cpp**  
  
## Vea también  
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [task\_group \(Clase\)](../Topic/task_group%20Class.md)   
 [structured\_task\_group \(Clase\)](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel\_for\_each \(Función\)](../Topic/parallel_for_each%20Function.md)