---
title: "C&#243;mo: Convertir un bucle OpenMP paralelo para usar el runtime de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convertir de OpenMP a Runtime de simultaneidad, bucles for paralelos"
  - "convertir de OpenMP a Runtime de simultaneidad, bucles paralelos"
  - "bucles for paralelos, convertir de OpenMP a Runtime de simultaneidad"
  - "bucles paralelos, convertir de OpenMP a Runtime de simultaneidad"
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir un bucle OpenMP paralelo para usar el runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo convertir un bucle básico que usa las directivas OpenMP [parallel](../../parallel/openmp/reference/parallel.md) y [for](../../parallel/openmp/reference/for-openmp.md) para utilizar el algoritmo [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) del runtime de simultaneidad.  
  
## Ejemplo  
 En este ejemplo se usan OpenMP y el runtime de simultaneidad para calcular el contador de números primos en una matriz de valores aleatorios.  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/CPP/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Using OpenMP...**  
**found 107254 prime numbers.**  
**Using the Concurrency Runtime...**  
**found 107254 prime numbers.** El algoritmo `parallel_for` y OpenMP 3.0 permiten que el tipo de índice sea un tipo entero con signo o un tipo entero sin signo.  El algoritmo `parallel_for` también se asegura de que el intervalo especificado no desborde un tipo con signo.  Las versiones 2.0 y 2.5 de OpenMP solo permiten los tipos enteros de índice con signo.  Además, OpenMP no valida el intervalo de índices.  
  
 La versión de este ejemplo que usa el runtime de simultaneidad también emplea un objeto [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) en lugar de la directiva [atomic](../../parallel/openmp/reference/atomic.md) para aumentar el valor del contador sin necesidad de sincronización.  
  
 Para obtener más información sobre `parallel_for` y otros algoritmos paralelos, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  Para obtener más información sobre la clase `combinable`, vea [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Ejemplo  
 En este ejemplo se modifica el anterior para actuar sobre un objeto [std::array](../../standard-library/array-class-stl.md) en lugar de actuar sobre una matriz nativa.  Dado que las versiones 2.0 y 2.5 de OpenMP solo permiten los tipos enteros de índice con signo en una construcción `parallel` `for`, no se pueden usar iteradores para obtener acceso a los elementos de un contenedor de la biblioteca de plantillas estándar \(STL\) en paralelo.  La biblioteca de patrones de procesamiento paralelo \(PPL\) proporciona el algoritmo [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md), que realiza las tareas, en paralelo, en un contenedor iterativo como los que proporciona STL.  Usa la misma lógica de creación de particiones que el algoritmo `parallel_for`.  El algoritmo `parallel_for_each` se parece al algoritmo [std::for\_each](../Topic/for_each.md), con la salvedad de que el algoritmo `parallel_for_each` ejecuta las tareas de forma simultánea.  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/CPP/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `concrt-omp-count-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-count\-primes.cpp**  
  
## Vea también  
 [Migrar de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)