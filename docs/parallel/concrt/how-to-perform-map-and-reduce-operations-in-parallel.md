---
title: 'Cómo: Realizar operaciones de asignación y reducción en paralelo'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: b73e46e63fc1b320a84322bf2b0efd7adf244ccb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651868"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Cómo: Realizar operaciones de asignación y reducción en paralelo

En este ejemplo se muestra cómo usar el [Concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) y [Concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmos y [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)clase para contar las apariciones de palabras en los archivos.

Un *mapa* operación aplica una función a cada valor de una secuencia. Un *reducir* operación combina los elementos de una secuencia en un valor. Puede usar la biblioteca estándar de C++ [std:: Transform](../../standard-library/algorithm-functions.md#transform) y [std:: Accumulate](../../standard-library/numeric-functions.md#accumulate) funciones para realizar map y reducir las operaciones. Sin embargo, si desea mejorar el rendimiento ante los diversos problemas que pueden surgir, use los algoritmos `parallel_transform` y `parallel_reduce` para realizar las operaciones map y reduce en paralelo, respectivamente. En algunos casos, puede usar `concurrent_unordered_map` para realizar map y reduce en una sola operación.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se cuentan las apariciones de las palabras en los archivos. Lo usa [std:: vector](../../standard-library/vector-class.md) para representar el contenido de dos archivos. La operación map calcula las apariciones de cada palabra en cada vector. La operación reduce suma los recuentos de palabras de los dos vectores.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-map-reduce.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc paralelo-map-reduce.cpp**

## <a name="robust-programming"></a>Programación sólida

En este ejemplo, puede usar la clase `concurrent_unordered_map` que se define en concurrent_unordered_map.h para realizar map y reduce en una sola operación.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

Por lo general, solo se ejecutan en paralelo los bucles internos o externos. Ejecute en paralelo el bucle interno si dispone de relativamente pocos archivos y cada uno de ellos contiene muchas palabras. Sin embargo, si dispone de un número razonable de archivos y cada uno de ellos contiene pocas palabras, ejecute en paralelo el bucle externo.

## <a name="see-also"></a>Vea también

[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform (función)](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce (función)](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
