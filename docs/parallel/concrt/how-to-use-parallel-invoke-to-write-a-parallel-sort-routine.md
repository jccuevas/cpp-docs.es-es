---
title: "Cómo: usar Parallel.Invoke para escribir una rutina de ordenación en paralelo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff14294236efc26b83d31ad185dc1cfd6329dbe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>Cómo: Usar parallel.invoke para escribir una rutina de ordenación en paralelo
Este documento describe cómo utilizar el [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) algoritmo para mejorar el rendimiento del algoritmo de ordenación bitónica. Este algoritmo divide de forma recursiva la secuencia de entrada en particiones ordenadas más pequeñas. Se puede ejecutar en paralelo porque cada operación de partición es independiente de las demás operaciones.  
  
 Aunque la ordenación bitónica es un ejemplo de un *red de ordenación* que ordena todas las combinaciones de secuencias de entrada, en este ejemplo se ordena secuencias cuyas longitudes son potencia de dos.  
  
> [!NOTE]
>  En este ejemplo se utiliza una rutina de ordenación paralela para la ilustración. También puede utilizar los algoritmos de ordenación integrados que proporciona la biblioteca PPL: [Concurrency:: parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [Concurrency:: parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), y [concurrency::parallel_ radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Para obtener más información, consulte [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="top"></a> Secciones  
 En este documentos se describen las tareas siguientes:  
  
- [Realizar la ordenación bitónica en serie](#serial)  
  
- [Usar parallel_invoke para realizar la ordenación bitónica en paralelo](#parallel)  
  
##  <a name="serial"></a>Realizar la ordenación bitónica en serie  
 En el siguiente ejemplo se muestra la versión en serie del algoritmo de ordenación bitónica. La función `bitonic_sort` divide la secuencia en dos particiones, ordena estas particiones en direcciones opuestas y, a continuación, combina los resultados. Esta función se llama a sí misma dos veces de forma recursiva para ordenar cada partición.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]  
  
 [[Arriba](#top)]  
  
##  <a name="parallel"></a>Usar parallel_invoke para realizar la ordenación bitónica en paralelo  
 En esta sección se describe cómo usar el algoritmo `parallel_invoke` para realizar el algoritmo de ordenación bitónica en paralelo.  
  
### <a name="procedures"></a>Procedimientos  
  
##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Para realizar el algoritmo de ordenación bitónica en paralelo  
  
1.  Agregue una directiva `#include` para el archivo de encabezado ppl.h.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]  
  
2.  Agregue una directiva `using` para el espacio de nombres `concurrency`.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]  
  
3.  Cree una nueva función, denominada `parallel_bitonic_mege`, que use el algoritmo `parallel_invoke` para combinar las secuencias en paralelo si hay suficiente cantidad de trabajo. De lo contrario, llame a `bitonic_merge` para combinar las secuencias en serie.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]  
  
4.  Realice un proceso similar al del paso anterior, pero en este caso para la función `bitonic_sort`.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]  
  
5.  Cree una versión sobrecargada de la función `parallel_bitonic_sort` que ordene la matriz en sentido ascendente.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]  
  
 El algoritmo `parallel_invoke` reduce la sobrecarga al realizar la última tarea de la serie en el contexto de llamada. Por ejemplo, en la función `parallel_bitonic_sort`, la primera tarea se ejecuta en un contexto independiente y la segunda tarea se ejecuta en el contexto de llamada.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]  
  
 El siguiente ejemplo completo realiza tanto las versiones en serie como en paralelo del algoritmo de ordenación bitónica. También imprime en la consola el tiempo necesario para realizar cada cálculo.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
```Output  
serial time: 4353  
parallel time: 1248  
```  
  
 [[Arriba](#top)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `parallel-bitonic-sort.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc parallel-bitonic-sort.cpp**  
  
## <a name="robust-programming"></a>Programación sólida  
 Este ejemplo se utiliza la `parallel_invoke` algoritmo en lugar de la [Concurrency:: task_group](reference/task-group-class.md) clase porque la duración de cada grupo de tareas no se extiende más allá de una función. Se recomienda usar `parallel_invoke` siempre que se pueda, ya que tiene menos sobrecarga de ejecución que los objetos `task group` y, por tanto, permite escribir código con mejor rendimiento.  
  
 Las versiones en paralelo de algunos algoritmos presentan mejor rendimiento cuando existe suficiente trabajo. Por ejemplo, la función `parallel_bitonic_merge` llama a la versión en serie, `bitonic_merge`, si existen 500 elementos o menos en la secuencia. También puede planear la estrategia global de ordenación según la cantidad de trabajo. Por ejemplo, puede ser más eficaz usar la versión en serie del algoritmo de ordenación rápida si la matriz contiene menos de 500 elementos, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]  
  
 Como con cualquier algoritmo paralelo, se recomienda generar un perfil y optimizar el código según corresponda.  
  
## <a name="see-also"></a>Vea también  
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel_invoke (función)](reference/concurrency-namespace-functions.md#parallel_invoke)

