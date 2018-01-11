---
title: "Cómo: usar la clase combinable para mejorar el rendimiento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dea28bd31812449e34bb481d316070f8f21aaede
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Cómo: Usar la clase combinable para mejorar el rendimiento
Este ejemplo muestra cómo utilizar el [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase para calcular la suma de los números en un [std:: Array](../../standard-library/array-class-stl.md) objetos que son primos. La clase `combinable` mejora el rendimiento eliminando el estado compartido.  
  
> [!TIP]
>  En algunos casos, la asignación en paralelo ([Concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) y reducir ([concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) puede proporcionar mejoras de rendimiento sobre `combinable`. Para obtener un ejemplo que usa asignación y reduce las operaciones para producir los mismos resultados que en este ejemplo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el [std:: Accumulate](../../standard-library/numeric-functions.md#accumulate) función para calcular la suma de los elementos de una matriz que son primos. En este ejemplo, `a` es un objeto `array` y la función `is_prime` determina si su valor de entrada es primo.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## <a name="example"></a>Ejemplo  

 En el siguiente ejemplo se muestra una manera sencilla de ejecutar el ejemplo anterior en paralelo. Este ejemplo se utiliza la [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo para procesar la matriz en paralelo y un [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) objeto para sincronizar el acceso a la `prime_sum` variable . Este ejemplo no se escala porque cada subproceso debe esperar a que el recurso compartido esté disponible.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se usa un objeto `combinable` para mejorar el rendimiento del ejemplo anterior. En este ejemplo se elimina la necesidad de usar los objetos de sincronización; se escala porque el objeto `combinable` permite a cada subproceso realizar su tarea independientemente.  
  
 Un objeto `combinable` se usa normalmente en dos pasos. Primero, genere una serie de cálculos específicos realizando el trabajo en paralelo. Luego, combine (o reduzca) los cálculos en un resultado final. Este ejemplo se utiliza la [concurrency::combinable::local](reference/combinable-class.md#local) método para obtener una referencia a la suma local. A continuación, utiliza el [concurrency::combinable::combine](reference/combinable-class.md#combine) método y un [std:: Plus](../../standard-library/plus-struct.md) objeto que se va a combinar los cálculos locales en el resultado final.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo completo calcula la suma de números primos consecutivamente y en paralelo. El ejemplo imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
```Output  
1709600813  
serial time: 6178 ms  
 
1709600813  
parallel time: 1638 ms  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `parallel-sum-of-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc parallel-sum-of-primes.cpp**  
  
## <a name="robust-programming"></a>Programación sólida  
 Para obtener un ejemplo que usa asignación y reduce las operaciones para producir los mismos resultados, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="see-also"></a>Vea también  
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable (clase)](../../parallel/concrt/reference/combinable-class.md)   
 [critical_section (clase)](../../parallel/concrt/reference/critical-section-class.md)
