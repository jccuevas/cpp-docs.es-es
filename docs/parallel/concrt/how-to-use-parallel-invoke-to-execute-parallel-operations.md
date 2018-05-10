---
title: 'Cómo: usar Parallel.Invoke para ejecutar operaciones paralelas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07c7a5248d5a132ae7b0542bfcedddee0c081753
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Cómo: Usar parallel.invoke para ejecutar operaciones paralelas
Este ejemplo muestra cómo utilizar el [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo para mejorar el rendimiento de un programa que realiza varias operaciones en un origen de datos compartido. Dado que ninguna de ellas modifica el origen, se pueden ejecutar en paralelo de manera sencilla.  

  
## <a name="example"></a>Ejemplo  
 Considere el ejemplo siguiente de código que crea una variable de tipo `MyDataType`, llama a una función para inicializar la variable y, a continuación, realiza operaciones largas en esos datos.  
  
 [!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]  
  
 Si las funciones `lengthy_operation1`, `lengthy_operation2` y `lengthy_operation3` no modifican la variable `MyDataType`, estas funciones se pueden ejecutar en paralelo sin modificaciones adicionales.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se modifica el ejemplo anterior para la ejecución en paralelo. El algoritmo `parallel_invoke` ejecuta cada tarea en paralelo y vuelve una vez finalizadas todas las tareas.  
  
 [!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se descarga *la Ilíada* de Homero de gutenberg.org y realiza varias operaciones en ese archivo. El ejemplo realiza primero estas operaciones en serie y, a continuación, realiza las mismas operaciones en paralelo.  
  
 [!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo.  
  
```Output  
Downloading 'The Iliad'...  
 
Running serial version... took 953 ms.  
Running parallel version... took 656 ms.  
 
The most common words that have five or more letters are:  
    their (953)  
    shall (444)  
    which (431)  
    great (398)  
    Hector (349)  
    Achilles (309)  
    through (301)  
    these (268)  
    chief (259)  
The longest sequence of words that have the same first letter is:  
    through the tempest to the tented  
The following palindromes appear in the text:  
    spots stops  
    speed deeps  
    keels sleek  
```  
  
 En este ejemplo se usa el algoritmo `parallel_invoke` para llamar a varias funciones que actúan sobre el mismo origen de datos. Puede usar el algoritmo `parallel_invoke` para llamar a cualquier conjunto de funciones en paralelo, no solo a los que actúan sobre los mismos datos.  
  
 Dado que el algoritmo `parallel_invoke` llama a cada función de trabajo en paralelo, el rendimiento está limitado por la función que tarda más tiempo en terminar (es decir, si el tiempo de ejecución procesa cada función en un procesador independiente). Si este ejemplo efectúa más tareas en paralelo que el número de procesadores disponibles, se pueden ejecutar varias tareas en cada procesador. En este caso, el rendimiento está limitado por el grupo de tareas que tarda más tiempo en finalizar.  
  
 Dado que este ejemplo realiza tres tareas en paralelo, no debe esperar que el rendimiento se escale en los equipos que tienen más de tres procesadores. Para mejorar el rendimiento, puede dividir las tareas más prolongadas en otras más pequeñas y ejecutarlas en paralelo.  
  
 Puede usar el `parallel_invoke` algoritmo en lugar de la [Concurrency:: task_group](reference/task-group-class.md) y [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) clases si no es necesario admita cancelación. Para obtener un ejemplo que compara el uso de la `parallel_invoke` algoritmo frente a grupos de tareas, consulte [Cómo: usar Parallel.Invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `parallel-word-mining.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **/ EHsc cl.exe /MD/DUNICODE /D_AFXDLL parallel-word-mining.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_invoke (función)](reference/concurrency-namespace-functions.md#parallel_invoke)


