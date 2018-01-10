---
title: "Cómo: convertir un bucle OpenMP que usa el control de excepciones para usar el Runtime de simultaneidad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2964c629ce8a3a83799278ac822b589992b4995
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Cómo: Convertir un bucle OpenMP que usa el control de excepciones para usar el runtime de simultaneidad
En este ejemplo se muestra cómo convertir de OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que realiza el control de excepciones para usar el mecanismo de control de excepciones de Runtime de simultaneidad.  
  
 En OpenMP, el mismo subproceso debe detectar y controlar en la misma región una excepción que se produce en una región paralela. Una excepción que escape de la región paralela será detectada por el controlador de excepciones no controladas, que finaliza el proceso de forma predeterminada.  
  

 En el Runtime de simultaneidad, cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un grupo de tareas como un [Concurrency:: task_group](reference/task-group-class.md) o [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objeto, o para un algoritmo paralelo como [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for), el runtime almacena esa excepción y calcula las referencias en el contexto que espera a que el grupo de tareas o el algoritmo finalice. Los grupos de tareas, el contexto de espera es el contexto que llama a [concurrency::task_group::wait](reference/task-group-class.md#wait), [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and _wait](reference/task-group-class.md#run_and_wait), o [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait). Para un algoritmo paralelo, el contexto que espera es el contexto que llamó a ese algoritmo. El runtime también detiene todas las tareas activas que están en el grupo de tareas, incluidas las que se encuentran en grupos de tareas secundarios, y descarta cualquier tarea que no se haya iniciado todavía.  


  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo controlar excepciones en una región `parallel` de OpenMP y en una llamada a `parallel_for`. El `do_work` función realiza una solicitud de asignación de memoria que no se realiza correctamente y, por tanto, se produce una excepción de tipo [std:: bad_alloc](../../standard-library/bad-alloc-class.md). En la versión que usa OpenMP, el subproceso que produce la excepción también debe detectarla. Es decir, cada iteración de un bucle paralelo de OpenMP debe controlar la excepción. En la versión que usa el runtime de simultaneidad, el subproceso principal detecta una excepción producida por otro subproceso.  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
Using OpenMP...  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
Using the Concurrency Runtime...  
An error of type 'class std::bad_alloc' occurred.  
```  
  
 En la versión de este ejemplo que usa OpenMP, la excepción se produce y controla en cada iteración del bucle. En la versión que usa el runtime de simultaneidad, el runtime almacena la excepción, detiene todas las tareas activas, descarta cualquier tarea que no se haya iniciado y calcula las referencias de la excepción en el contexto que llama a `parallel_for`.  
  
 Si necesita que la versión que usa OpenMP termine después de producirse la excepción, podría usar una marca booleana para indicar a otras iteraciones del bucle que se produjo el error. Como en el ejemplo en el tema [Cómo: convertir un bucle OpenMP que cancelación para usar el Runtime de simultaneidad usa](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), iteraciones del bucle posteriores no haría nada si se establece la marca. Por el contrario, si necesita que el bucle que usa el runtime de simultaneidad continúe después de que se produzca la excepción, controle la excepción en el cuerpo del bucle paralelo propiamente dicho.  
  
 Otros componentes del runtime de simultaneidad, como los agentes asincrónicos y las tareas ligeras, no transportan excepciones. En su lugar, el controlador de excepciones no controladas, que de forma predeterminada finaliza el proceso, detecta las excepciones no controladas. Para obtener más información sobre el control de excepciones, vea [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Para obtener más información acerca de `parallel_for` y otros algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `concrt-omp-exceptions.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc/OpenMP concrt-omp-exceptions.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Migrar de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)

