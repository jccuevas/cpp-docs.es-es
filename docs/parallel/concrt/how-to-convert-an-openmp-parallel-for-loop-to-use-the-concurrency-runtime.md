---
title: 'Cómo: Convertir un bucle OpenMP paralelo para usar el runtime de simultaneidad'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 2d96ba23582368fe72e61003823826a6f3ab807a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141761"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Cómo: Convertir un bucle OpenMP paralelo para usar el runtime de simultaneidad

En este ejemplo se muestra cómo convertir un bucle básico que usa las directivas [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) y [for de](../../parallel/openmp/reference/for-openmp.md) OpenMP para usar el algoritmo Runtime de simultaneidad [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .

## <a name="example---prime-count"></a>Ejemplo: número primo

En este ejemplo se usan OpenMP y el runtime de simultaneidad para calcular el contador de números primos en una matriz de valores aleatorios.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

El algoritmo `parallel_for` y OpenMP 3.0 permiten que el tipo de índice sea un tipo entero con signo o un tipo entero sin signo. El algoritmo `parallel_for` también se asegura de que el intervalo especificado no desborde un tipo con signo. Las versiones 2.0 y 2.5 de OpenMP solo permiten los tipos enteros de índice con signo. Además, OpenMP no valida el intervalo de índices.

La versión de este ejemplo que usa la Runtime de simultaneidad también usa un objeto [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) en lugar de la directiva [atómica](../../parallel/openmp/reference/atomic.md) para incrementar el valor del contador sin necesidad de sincronización.

Para obtener más información sobre `parallel_for` y otros algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md). Para obtener más información sobre la clase `combinable`, vea [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example---use-stdarray"></a>Ejemplo: uso de STD:: Array

Este ejemplo modifica el anterior para actuar sobre un objeto [STD:: Array](../../standard-library/array-class-stl.md) en lugar de en una matriz nativa. Dado que las versiones 2,0 y 2,5 de OpenMP solo permiten tipos de índice enteros con signo en una construcción `parallel_for`, no puede usar iteradores para tener C++ acceso a los elementos de un contenedor de la biblioteca estándar en paralelo. La biblioteca de patrones de procesamiento paralelo (PPL) proporciona el algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , que realiza tareas, en paralelo, en un contenedor iterativo como los que C++ proporciona la biblioteca estándar. Usa la misma lógica de creación de particiones que el algoritmo `parallel_for`. El algoritmo `parallel_for_each` es similar al C++ algoritmo [std:: For_each](../../standard-library/algorithm-functions.md#for_each) de la biblioteca estándar, con la excepción de que el algoritmo `parallel_for_each` ejecuta las tareas simultáneamente.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `concrt-omp-count-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc/OpenMP concrt-OMP-Count-primes. cpp**

## <a name="see-also"></a>Consulte también

[Migración de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)
