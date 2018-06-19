---
title: 'Cómo: escribir un bucle parallel_for_each | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ba40b7d9ea93e73d9d18d3548b0c0f34c6411f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686014"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>Cómo: Escribir un bucle parallel_for_each
Este ejemplo muestra cómo utilizar el [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo para calcular el recuento de números primos en un [std:: Array](../../standard-library/array-class-stl.md) objeto en paralelo.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se calcula dos veces el recuento de números primos en una matriz. El ejemplo usa primero el [std:: for_each](../../standard-library/algorithm-functions.md#for_each) algoritmo para calcular el recuento en serie. A continuación, en el ejemplo se usa el algoritmo `parallel_for_each` para realizar la misma tarea en paralelo. También se imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
```Output  
serial version:  
found 17984 prime numbers  
took 6115 ms  
 
parallel version:  
found 17984 prime numbers  
took 1653 ms  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `parallel-count-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc parallel-count-primes.cpp**  
  
## <a name="robust-programming"></a>Programación sólida  
 La expresión lambda que el ejemplo pasa al algoritmo `parallel_for_each` usa la función `InterlockedIncrement` para permitir a las iteraciones paralelas del bucle incrementar el contador simultáneamente. Si usa funciones como `InterlockedIncrement` para sincronizar el acceso a los recursos compartidos, pueden presentarse cuellos de botella de rendimiento en el código. Puede usar un mecanismo de sincronización sin bloqueos, por ejemplo, el [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) (clase), para eliminar el acceso simultáneo a los recursos compartidos. Para obtener un ejemplo que usa el `combinable` clase de esta manera, consulte [Cómo: usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).  
  
## <a name="see-also"></a>Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for_each (función)](reference/concurrency-namespace-functions.md#parallel_for_each)


