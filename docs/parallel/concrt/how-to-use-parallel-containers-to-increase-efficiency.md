---
title: 'Cómo: usar contenedores paralelos para aumentar la eficacia | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71a4aee5664864b5a9c803ac5048e8e5b5eacf0a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383316"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Cómo: Usar contenedores paralelos para aumentar la eficacia

En este tema se muestra cómo se usan contenedores paralelos para almacenar de forma eficaz los datos y tener acceso a ellos en paralelo.

En el código de ejemplo se calcula el conjunto de números primos y de números de Carmichael en paralelo. A continuación, el código calcula los factores primos de cada número de Carmichael.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la función `is_prime`, que determina si un valor de entrada es un número primo, y la función `is_carmichael`, que determina si el valor de entrada es un número de Carmichael.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se usan las funciones `is_prime` e `is_carmichael` para calcular los conjuntos de números primos y números de Carmichael. El ejemplo se usa el [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) y [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmos para calcular cada conjunto en paralelo. Para obtener más información acerca de los algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

Este ejemplo se usa un [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) números del objeto para almacenar el conjunto de Carmichael porque más adelante usará ese objeto como una cola de trabajo. Usa un [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objeto para almacenar el conjunto de números primos porque más adelante creará una iteración a través de este conjunto para buscar factores primos.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra la función `prime_factors_of`, que usa la división por tentativa para encontrar todos los factores primos del valor especificado.

Esta función usa el [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo para recorrer en iteración la colección de números primos. El objeto `concurrent_vector` permite al bucle paralelo agregar simultáneamente los factores primos al resultado.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>Ejemplo

En este ejemplo se procesa cada elemento de la cola de números de Carmichael llamando a la función `prime_factors_of` para calcular sus factores primos. En el ejemplo se usa un grupo de tareas para realizar este trabajo en paralelo. Para obtener más información acerca de los grupos de tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

En este ejemplo se imprimen los factores primos de cada número de Carmichael si dicho número tiene más de cuatro factores primos.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el ejemplo completo, en el que se usan los contenedores paralelos para calcular los factores primos de los números de Carmichael.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `carmichael-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc carmichael-primes.cpp**

## <a name="see-also"></a>Vea también

[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector (clase)](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue (clase)](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke (función)](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group (clase)](reference/task-group-class.md)
