---
title: "Parallel Patterns Library (PPL) | Microsoft Docs"
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
  - "Parallel Patterns Library (PPL)"
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# Parallel Patterns Library (PPL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La Biblioteca de patrones de procesamiento paralelo (PPL) proporciona un modelo de programación imperativo que favorece la escalabilidad y facilidad de uso para desarrollar aplicaciones simultáneas. PPL se basa en los componentes de administración de recursos y programación del Runtime de simultaneidad. Eleva el nivel de abstracción entre el código de aplicación y el mecanismo de subprocesamiento subyacente proporcionando contenedores y algoritmos genéricos, con seguridad de tipos, que actúan sobre los datos en paralelo. PPL también permite desarrollar aplicaciones que escalan proporcionando alternativas al estado compartido.  
  
 PPL proporciona las características siguientes.  
  
- *Paralelismo de tareas*: un mecanismo que se basa en el grupo de subprocesos de Windows para ejecutar varios elementos de trabajo (tareas) en paralelo  
  
- *Algoritmos paralelos*: algoritmos genéricos que se basa en el Runtime de simultaneidad para actuar en colecciones de datos en paralelo  
  
- *Contenedores y objetos paralelos*: tipos de contenedor genéricos que proporcionan acceso simultáneo seguro a sus elementos  
  
## <a name="example"></a>Ejemplo  
 PPL proporciona un modelo de programación que se parece al de la Biblioteca de plantillas estándar (STL). En el ejemplo siguiente se muestran muchas características de PPL: Calcula varios números de Fibonacci en serie y en paralelo. Ambos cálculos actúan sobre un [std:: Array](../../standard-library/array-class-stl.md) objeto. También se imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 La versión en serie usa STL [std:: for_each](../Topic/for_each.md) algoritmo para atravesar la matriz y almacena los resultados en un [std:: vector](vector%20Class.md) objeto. La versión en paralelo realiza la misma tarea, pero usa la biblioteca PPL [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) algoritmo y almacena los resultados en un [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objeto. La clase `concurrent_vector` permite que cada iteración del bucle agregue los elementos de forma simultánea, sin el requisito de sincronizar el acceso de escritura en el contenedor.  
  
 Dado que `parallel_for_each` actúa de manera simultánea, la versión del cálculo en paralelo de este ejemplo debe ordenar el objeto `concurrent_vector` para generar los mismos resultados que la versión del cálculo en serie.  
  
 Observe que en el ejemplo se usa un método sencillo para calcular los números de Fibonacci; sin embargo, este método muestra cómo el Runtime de simultaneidad puede mejorar el rendimiento en el caso de cálculos largos.  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/CPP/parallel-patterns-library-ppl_1.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
```Output  
serial time: 9250 ms  
parallel time: 5726 ms  
 
fib(24): 46368  
fib(26): 121393  
fib(41): 165580141  
fib(42): 267914296  
```  
  
 Cada iteración del bucle requiere una cantidad de tiempo diferente para finalizar. La operación que finaliza en último lugar limita el rendimiento de `parallel_for_each`. Por consiguiente, no debería esperar mejoras de rendimiento lineales entre las versiones en serie y en paralelo de este ejemplo.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Describe el rol de las tareas y los grupos de tareas en la biblioteca PPL.|  
|[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)|Se describe cómo usar algoritmos paralelos, como `parallel_for` y `parallel_for_each`.|  
|[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)|Se describen los distintos objetos y contenedores paralelos que proporciona PPL.|  
|[Cancelación](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)|Explica cómo cancelar el trabajo realizado por un algoritmo paralelo.|  
|[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)|Se describe el Runtime de simultaneidad, que simplifica la programación en paralelo, y contiene vínculos a los temas relacionados.|

