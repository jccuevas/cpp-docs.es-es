---
title: 'Cómo: Usar la clase combinable para mejorar el rendimiento'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: db27a791b2b92102118606712db4cbd2920f9619
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142438"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Cómo: Usar la clase combinable para mejorar el rendimiento

En este ejemplo se muestra cómo usar la clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) para calcular la suma de los números de un objeto [STD:: Array](../../standard-library/array-class-stl.md) que son primos. La clase `combinable` mejora el rendimiento eliminando el estado compartido.

> [!TIP]
> En algunos casos, la asignación paralela ([simultaneidad::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) y la reducción ([simultaneidad:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) pueden proporcionar mejoras de rendimiento respecto a `combinable`. Para obtener un ejemplo en el que se usan las operaciones de asignación y reducción para producir los mismos resultados que en este ejemplo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="example---accumulate"></a>Ejemplo: acumular

En el ejemplo siguiente se usa la función [STD:: ACCUMULATE](../../standard-library/numeric-functions.md#accumulate) para calcular la suma de los elementos de una matriz que son primos. En este ejemplo, `a` es un objeto `array` y la función `is_prime` determina si su valor de entrada es primo.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>Ejemplo: parallel_for_each

En el siguiente ejemplo se muestra una manera sencilla de ejecutar el ejemplo anterior en paralelo. En este ejemplo se usa el algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) para procesar la matriz en paralelo y un objeto [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) para sincronizar el acceso a la variable de `prime_sum`. Este ejemplo no se escala porque cada subproceso debe esperar a que el recurso compartido esté disponible.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>Ejemplo: combinable

En el siguiente ejemplo se usa un objeto `combinable` para mejorar el rendimiento del ejemplo anterior. En este ejemplo se elimina la necesidad de usar los objetos de sincronización; se escala porque el objeto `combinable` permite a cada subproceso realizar su tarea independientemente.

Un objeto `combinable` se usa normalmente en dos pasos. Primero, genere una serie de cálculos específicos realizando el trabajo en paralelo. Luego, combine (o reduzca) los cálculos en un resultado final. En este ejemplo se usa el método [Concurrency:: combinable:: local](reference/combinable-class.md#local) para obtener una referencia a la suma local. A continuación, usa el método [Concurrency:: combinable:: Combine](reference/combinable-class.md#combine) y un objeto [STD::p UGM](../../standard-library/plus-struct.md) para combinar los cálculos locales en el resultado final.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>Ejemplo: serie y paralelo

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

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-sum-of-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Parallel-SUM-of-primes. cpp**

## <a name="robust-programming"></a>Programación sólida

Para obtener un ejemplo que usa las operaciones de asignación y reducción para producir los mismos resultados, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="see-also"></a>Consulte también

[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable (clase)](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section (clase)](../../parallel/concrt/reference/critical-section-class.md)
