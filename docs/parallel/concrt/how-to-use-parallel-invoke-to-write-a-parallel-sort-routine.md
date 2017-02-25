---
title: "C&#243;mo: Usar parallel.invoke para escribir una rutina de ordenaci&#243;n en paralelo | Microsoft Docs"
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
  - "task_handle (clase), ejemplo"
  - "task_group (clase), ejemplo"
  - "make_task (función), ejemplo"
  - "structured_task_group (clase), ejemplo"
  - "mejorar el rendimiento paralelo con grupos de tareas [Runtime de simultaneidad]"
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# C&#243;mo: Usar parallel.invoke para escribir una rutina de ordenaci&#243;n en paralelo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describe cómo usar el algoritmo [parallel\_invoke](../Topic/parallel_invoke%20Function.md) para mejorar el rendimiento del algoritmo de ordenación bitónica.  Este algoritmo divide de forma recursiva la secuencia de entrada en particiones ordenadas más pequeñas.  Se puede ejecutar en paralelo porque cada operación de partición es independiente de las demás operaciones.  
  
 Aunque la ordenación bitónica es un ejemplo de una *red de ordenación* que ordena todas las combinaciones de secuencias de entrada, en este ejemplo se ordenan secuencias cuyas longitudes son potencia de dos.  
  
> [!NOTE]
>  En este ejemplo se utiliza una rutina de ordenación paralela para la ilustración.  También puede utilizar los algoritmos de ordenación integrados que proporciona PPL: [concurrency::parallel\_sort](../Topic/parallel_sort%20Function.md), [concurrency::parallel\_buffered\_sort](../Topic/parallel_buffered_sort%20Function.md) y [concurrency::parallel\_radixsort](../Topic/parallel_radixsort%20Function.md).  Para obtener más información, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="top"></a> Secciones  
 En este documentos se describen las tareas siguientes:  
  
-   [Realizar la ordenación bitónica en serie](#serial)  
  
-   [Usar parallel\_invoke para realizar la ordenación bitónica en paralelo](#parallel)  
  
##  <a name="serial"></a> Realizar la ordenación bitónica en serie  
 En el siguiente ejemplo se muestra la versión en serie del algoritmo de ordenación bitónica.  La función `bitonic_sort` divide la secuencia en dos particiones, ordena estas particiones en direcciones opuestas y, a continuación, combina los resultados.  Esta función se llama a sí misma dos veces de forma recursiva para ordenar cada partición.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]  
  
 \[[Arriba](#top)\]  
  
##  <a name="parallel"></a> Usar parallel\_invoke para realizar la ordenación bitónica en paralelo  
 En esta sección se describe cómo usar el algoritmo `parallel_invoke` para realizar el algoritmo de ordenación bitónica en paralelo.  
  
### Procedimientos  
  
##### Para realizar el algoritmo de ordenación bitónica en paralelo  
  
1.  Agregue una directiva `#include` para el archivo de encabezado ppl.h.  
  
     [!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]  
  
2.  Agregue una directiva `using` para el espacio de nombres `concurrency`.  
  
     [!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]  
  
3.  Cree una nueva función, denominada `parallel_bitonic_mege`, que use el algoritmo `parallel_invoke` para combinar las secuencias en paralelo si hay suficiente cantidad de trabajo.  De lo contrario, llame a `bitonic_merge` para combinar las secuencias en serie.  
  
     [!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]  
  
4.  Realice un proceso similar al del paso anterior, pero en este caso para la función `bitonic_sort`.  
  
     [!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]  
  
5.  Cree una versión sobrecargada de la función `parallel_bitonic_sort` que ordene la matriz en sentido ascendente.  
  
     [!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]  
  
 El algoritmo `parallel_invoke` reduce la sobrecarga al realizar la última tarea de la serie en el contexto de llamada.  Por ejemplo, en la función `parallel_bitonic_sort`, la primera tarea se ejecuta en un contexto independiente y la segunda tarea se ejecuta en el contexto de llamada.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]  
  
 El siguiente ejemplo completo realiza tanto las versiones en serie como en paralelo del algoritmo de ordenación bitónica.  También imprime en la consola el tiempo necesario para realizar cada cálculo.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
  **serial time: 4353**  
**parallel time: 1248** \[[Arriba](#top)\]  
  
## Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o en un archivo denominado `parallel-bitonic-sort.cpp` y ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-bitonic\-sort.cpp**  
  
## Programación sólida  
 En este ejemplo se usa el algoritmo `parallel_invoke` en lugar de la clase [concurrency::task\_group](../Topic/task_group%20Class.md) porque la duración de cada grupo de tareas no se extiende más allá de una función.  Se recomienda usar `parallel_invoke` siempre que se pueda, ya que tiene menos sobrecarga de ejecución que los objetos `task group` y, por tanto, permite escribir código con mejor rendimiento.  
  
 Las versiones en paralelo de algunos algoritmos presentan mejor rendimiento cuando existe suficiente trabajo.  Por ejemplo, la función `parallel_bitonic_merge` llama a la versión en serie, `bitonic_merge`, si existen 500 elementos o menos en la secuencia.  También puede planear la estrategia global de ordenación según la cantidad de trabajo.  Por ejemplo, puede ser más eficaz usar la versión en serie del algoritmo de ordenación rápida si la matriz contiene menos de 500 elementos, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]  
  
 Como con cualquier algoritmo paralelo, se recomienda generar un perfil y optimizar el código según corresponda.  
  
## Vea también  
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel\_invoke \(Función\)](../Topic/parallel_invoke%20Function.md)