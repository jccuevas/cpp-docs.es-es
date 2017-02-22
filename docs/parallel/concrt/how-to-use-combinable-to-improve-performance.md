---
title: "C&#243;mo: Usar la clase combinable para mejorar el rendimiento | Microsoft Docs"
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
  - "combinable (clase), ejemplo"
  - "mejorar el rendimiento paralelo con la clase combinable [Runtime de simultaneidad]"
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Usar la clase combinable para mejorar el rendimiento
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo usar la clase [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) para calcular la suma de los números de un objeto [std::array](../../standard-library/array-class-stl.md) que son primos.  La clase `combinable` mejora el rendimiento eliminando el estado compartido.  
  
> [!TIP]
>  En algunos casos, la asignación en paralelo \([concurrency::parallel\_transform](../Topic/parallel_transform%20Function.md)\) y la reducción \([concurrency:: parallel\_reduce](../Topic/parallel_reduce%20Function.md)\) pueden proporcionar mejoras de rendimiento respecto a `combinable`.  Puede ver un ejemplo que utiliza las operaciones de asignación y reducción para producir los mismos resultados que en este ejemplo en [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## Ejemplo  
 En el siguiente ejemplo se usa la función [std::accumulate](../Topic/accumulate.md) para calcular la suma de los elementos de una matriz que son primos.  En este ejemplo, `a` es un objeto `array` y la función `is_prime` determina si su valor de entrada es primo.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se muestra una manera sencilla de ejecutar el ejemplo anterior en paralelo.  En este ejemplo se usa el algoritmo [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) para procesar la matriz en paralelo y un objeto [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) para sincronizar el acceso a la variable `prime_sum`.  Este ejemplo no se escala porque cada subproceso debe esperar a que el recurso compartido esté disponible.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se usa un objeto `combinable` para mejorar el rendimiento del ejemplo anterior.  En este ejemplo se elimina la necesidad de usar los objetos de sincronización; se escala porque el objeto `combinable` permite a cada subproceso realizar su tarea independientemente.  
  
 Un objeto `combinable` se usa normalmente en dos pasos.  Primero, genere una serie de cálculos específicos realizando el trabajo en paralelo.  Luego, combine \(o reduzca\) los cálculos en un resultado final.  En este ejemplo se usa el método [concurrency::combinable::local](../Topic/combinable::local%20Method.md) para obtener una referencia a la suma local.  A continuación, se usa el método [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) y un objeto [std::plus](../../standard-library/plus-struct.md) para combinar los cálculos locales en el resultado final.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## Ejemplo  
 El siguiente ejemplo completo calcula la suma de números primos consecutivamente y en paralelo.  El ejemplo imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
  **1709600813**  
**serial time: 6178 ms**  
**1709600813**  
**parallel time: 1638 ms**   
## Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o en un archivo denominado `parallel-sum-of-primes.cpp` y ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-sum\-of\-primes.cpp**  
  
## Programación eficaz  
 Para consultar un ejemplo que usa las operaciones de asignación y reducción para producir los mismos resultados, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## Vea también  
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Clase combinable](../../parallel/concrt/reference/combinable-class.md)   
 [critical\_section \(Clase\)](../../parallel/concrt/reference/critical-section-class.md)