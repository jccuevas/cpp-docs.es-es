---
title: 'Cómo: Realizar operaciones de asignación y reducción en paralelo'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: 599e46c05a91a1f2ea6e317fe024d3c98a78977f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141707"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Cómo: Realizar operaciones de asignación y reducción en paralelo

En este ejemplo se muestra cómo usar los algoritmos Concurrency [::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) y [concurrency::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) y la clase [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) para contar las apariciones de las palabras en los archivos.

Una operación de *asignación* aplica una función a cada valor de una secuencia. Una operación de *reducción* combina los elementos de una secuencia en un valor. Puede usar las funciones C++ [STD:: transform](../../standard-library/algorithm-functions.md#transform) y [STD:: ACCUMULATE](../../standard-library/numeric-functions.md#accumulate) de la biblioteca estándar para realizar operaciones de asignación y reducción. Sin embargo, si desea mejorar el rendimiento ante los diversos problemas que pueden surgir, use los algoritmos `parallel_transform` y `parallel_reduce` para realizar las operaciones map y reduce en paralelo, respectivamente. En algunos casos, puede usar `concurrent_unordered_map` para realizar map y reduce en una sola operación.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se cuentan las apariciones de las palabras en los archivos. Utiliza [STD:: Vector](../../standard-library/vector-class.md) para representar el contenido de dos archivos. La operación map calcula las apariciones de cada palabra en cada vector. La operación reduce suma los recuentos de palabras de los dos vectores.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-map-reduce.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Parallel-Map-reduce. cpp**

## <a name="robust-programming"></a>Programación sólida

En este ejemplo, puede usar la clase `concurrent_unordered_map` que se define en concurrent_unordered_map.h para realizar map y reduce en una sola operación.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

Por lo general, solo se ejecutan en paralelo los bucles internos o externos. Ejecute en paralelo el bucle interno si dispone de relativamente pocos archivos y cada uno de ellos contiene muchas palabras. Sin embargo, si dispone de un número razonable de archivos y cada uno de ellos contiene pocas palabras, ejecute en paralelo el bucle externo.

## <a name="see-also"></a>Consulte también

[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform función)](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce función)](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
