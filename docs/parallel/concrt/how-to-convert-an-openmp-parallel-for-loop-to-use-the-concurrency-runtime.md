---
title: Procedimiento Convertir un bucle usar el Runtime de simultaneidad OpenMP paralelo
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: bc408465f34f0558e9f426ae35b83d4610898414
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413897"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Procedimiento Convertir un bucle usar el Runtime de simultaneidad OpenMP paralelo

En este ejemplo se muestra cómo convertir un bucle básico que usa el OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) y [para](../../parallel/openmp/reference/for-openmp.md) directivas para usar el Runtime de simultaneidad [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo.

## <a name="example"></a>Ejemplo

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

La versión de este ejemplo que usa el Runtime de simultaneidad también utiliza un [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) objeto en lugar de la [atómica](../../parallel/openmp/reference/atomic.md) directiva se va a incrementar el valor del contador sin necesidad de sincronización.

Para obtener más información acerca de `parallel_for` y otros algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md). Para obtener más información sobre la `combinable` de clases, vea [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example"></a>Ejemplo

En este ejemplo modifica el ejemplo anterior para actuar sobre un [std:: Array](../../standard-library/array-class-stl.md) en lugar del objeto en una matriz nativa. Debido a que las versiones 2.0 y 2.5 de OpenMP se permiten para firmados solo en tipos de índice entero un `parallel_for` construcción, no se puede usar iteradores para tener acceso a los elementos de un contenedor de la biblioteca estándar de C++ en paralelo. La biblioteca de patrones paralelos (PPL) proporciona la [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmo, que realiza las tareas, en paralelo, en un contenedor iterativo como los proporcionados por el C++ biblioteca estándar. Usa la misma lógica de creación de particiones que el algoritmo `parallel_for`. El `parallel_for_each` algoritmo es similar a la C++ biblioteca estándar de [std:: for_each](../../standard-library/algorithm-functions.md#for_each) algoritmo, salvo que el `parallel_for_each` algoritmo ejecuta las tareas de forma simultánea.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `concrt-omp-count-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe /EHsc /openmp concrt-omp-count-primes.cpp**

## <a name="see-also"></a>Vea también

[Migración de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)
