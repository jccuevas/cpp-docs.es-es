---
title: "C&#243;mo: Usar contenedores paralelos para aumentar la eficacia | Microsoft Docs"
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
  - "mejorar la eficacia con contenedores paralelos [Runtime de simultaneidad]"
  - "concurrent_queue (clase), ejemplos"
  - "concurrent_vector (clase), ejemplos"
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Usar contenedores paralelos para aumentar la eficacia
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo se usan contenedores paralelos para almacenar de forma eficaz los datos y tener acceso a ellos en paralelo.  
  
 En el código de ejemplo se calcula el conjunto de números primos y de números de Carmichael en paralelo.  A continuación, el código calcula los factores primos de cada número de Carmichael.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra la función `is_prime`, que determina si un valor de entrada es un número primo, y la función `is_carmichael`, que determina si el valor de entrada es un número de Carmichael.  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se usan las funciones `is_carmichael` e `is_prime` para calcular los conjuntos de números primos y números de Carmichael.  En el ejemplo se usan los algoritmos [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) y [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) para calcular cada conjunto en paralelo.  Para obtener más información acerca de los algoritmos paralelos, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
 En este ejemplo se usa un objeto [concurrency::concurrent\_queue](../../parallel/concrt/reference/concurrent-queue-class.md) para almacenar el conjunto de números de Carmichael porque más adelante se usará ese objeto como cola de trabajo.  Se usa un objeto [concurrency::concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md) para almacenar el conjunto de números primos porque más adelante se recorrerá en iteración este conjunto para buscar factores primos.  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se muestra la función `prime_factors_of`, que usa la división por tentativa para encontrar todos los factores primos del valor especificado.  
  
 En esta función se usa el algoritmo [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) para recorrer en iteración la colección de números primos.  El objeto `concurrent_vector` permite al bucle paralelo agregar simultáneamente los factores primos al resultado.  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## Ejemplo  
 En este ejemplo se procesa cada elemento de la cola de números de Carmichael llamando a la función `prime_factors_of` para calcular sus factores primos.  En el ejemplo se usa un grupo de tareas para realizar este trabajo en paralelo.  Para obtener más información acerca de los grupos de tareas, vea [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 En este ejemplo se imprimen los factores primos de cada número de Carmichael si dicho número tiene más de cuatro factores primos.  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## Ejemplo  
 En el código siguiente se muestra el ejemplo completo, en el que se usan los contenedores paralelos para calcular los factores primos de los números de Carmichael.  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/CPP/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo.  
  
  **Prime factors of 9890881 are: 7 11 13 41 241.**  
**Prime factors of 825265 are: 5 7 17 19 73.**  
**Prime factors of 1050985 are: 5 13 19 23 37.**   
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `carmichael-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc carmichael\-primes.cpp**  
  
## Vea también  
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Clase concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [Clase concurrent\_queue](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel\_invoke \(Función\)](../Topic/parallel_invoke%20Function.md)   
 [parallel\_for \(Función\)](../Topic/parallel_for%20Function.md)   
 [task\_group \(Clase\)](../Topic/task_group%20Class.md)