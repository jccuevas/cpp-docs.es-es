---
title: 'Cómo: Escribir un bucle parallel_for_each'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: 10c281b7db92e2706b20a1c7377fcdb9d924152d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141876"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>Cómo: Escribir un bucle parallel_for_each

En este ejemplo se muestra cómo usar el algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) para calcular el recuento de números primos en un objeto [STD:: Array](../../standard-library/array-class-stl.md) en paralelo.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se calcula dos veces el recuento de números primos en una matriz. En primer lugar, el ejemplo usa el algoritmo [STD:: for_each](../../standard-library/algorithm-functions.md#for_each) para calcular el recuento en serie. A continuación, en el ejemplo se usa el algoritmo `parallel_for_each` para realizar la misma tarea en paralelo. También se imprime en la consola el tiempo necesario para realizar ambos cálculos.

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

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-count-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Parallel-Count-primes. cpp**

## <a name="robust-programming"></a>Programación sólida

La expresión lambda que el ejemplo pasa al algoritmo `parallel_for_each` usa la función `InterlockedIncrement` para permitir a las iteraciones paralelas del bucle incrementar el contador simultáneamente. Si usa funciones como `InterlockedIncrement` para sincronizar el acceso a los recursos compartidos, pueden presentarse cuellos de botella de rendimiento en el código. Puede usar un mecanismo de sincronización sin bloqueos, por ejemplo, la clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) , para eliminar el acceso simultáneo a los recursos compartidos. Para obtener un ejemplo en el que se usa la clase `combinable` de esta manera, vea [Cómo: usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Consulte también

[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each función)](reference/concurrency-namespace-functions.md#parallel_for_each)
