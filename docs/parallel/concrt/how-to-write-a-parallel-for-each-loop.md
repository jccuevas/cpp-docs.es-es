---
title: "C&#243;mo: Escribir un bucle parallel_for_each | Microsoft Docs"
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
  - "escribir un bucle parallel_for_each [Runtime de simultaneidad]"
  - "parallel_for_each (función), ejemplo"
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Escribir un bucle parallel_for_each
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo usar el algoritmo [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) para calcular el recuento de números primos en un objeto [std::array](../../standard-library/array-class-stl.md) en paralelo.  
  
## Ejemplo  
 En el siguiente ejemplo se calcula dos veces el recuento de números primos en una matriz.  En el ejemplo se usa primero el algoritmo [std::for\_each](../Topic/for_each.md) para calcular el contador consecutivamente.  A continuación, en el ejemplo se usa el algoritmo `parallel_for_each` para realizar la misma tarea en paralelo.  También se imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
  **serial version:**  
**found 17984 prime numbers**  
**took 6115 ms**  
**parallel version:**  
**found 17984 prime numbers**  
**took 1653 ms**   
## Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o en un archivo denominado `parallel-count-primes.cpp` y ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-count\-primes.cpp**  
  
## Programación eficaz  
 La expresión lambda que el ejemplo pasa al algoritmo `parallel_for_each` usa la función `InterlockedIncrement` para permitir a las iteraciones paralelas del bucle incrementar el contador simultáneamente.  Si usa funciones como `InterlockedIncrement` para sincronizar el acceso a los recursos compartidos, pueden presentarse cuellos de botella de rendimiento en el código.  Puede usar un mecanismo de sincronización sin bloqueos, por ejemplo, la clase [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md), para eliminar el acceso simultáneo a los recursos compartidos.  Para consultar un ejemplo en el que se usa la clase `combinable` de esta forma, vea [Cómo: Usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).  
  
## Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for\_each \(Función\)](../Topic/parallel_for_each%20Function.md)