---
title: 'Cómo: Convertir un bucle OpenMP que usa una variable de reducción para usar el Runtime de simultaneidad'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: ee0a600f4234c3ebf4681ad92b5e3623be5665c3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141261"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Cómo: Convertir un bucle OpenMP que usa una variable de reducción para usar el Runtime de simultaneidad

En este ejemplo se muestra cómo convertir un bucle[for de](../../parallel/openmp/reference/for-openmp.md) OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)for que utiliza la cláusula [reduction](../../parallel/openmp/reference/reduction.md) para usar el Runtime de simultaneidad.

La cláusula OpenMP `reduction` permite especificar una o más variables privadas de subprocesos que están sujetas a una operación de reducción al final de la región paralela. OpenMP predefine un conjunto de operadores de reducción. Cada variable de reducción debe ser un escalar (por ejemplo, `int`, `long` y `float`). OpenMP también define varias restricciones sobre cómo se usan las variables de reducción en una región paralela.

La biblioteca de patrones de procesamiento paralelo (PPL) proporciona la clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) , que proporciona almacenamiento local de subprocesos reutilizable que permite realizar cálculos específicos y, a continuación, combinar estos cálculos en un resultado final. La clase `combinable` es una plantilla que actúa en los tipos escalares y complejos. Para usar la clase `combinable`, realice subcálculos en el cuerpo de una construcción paralela y, a continuación, llame al método [Concurrency:: combinable:: Combine](reference/combinable-class.md#combine) o [Concurrency:: combinable:: combine_each](reference/combinable-class.md#combine_each) para generar el resultado final. Los métodos `combine` y `combine_each` toman una *función combine* que especifica cómo combinar cada par de elementos. Por consiguiente, la clase `combinable` no se limita a un conjunto fijo de operadores de reducción.

## <a name="example"></a>Ejemplo

En este ejemplo se usa OpenMP y el runtime de simultaneidad para calcular la suma de los 35 primeros números de Fibonacci.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Para obtener más información sobre la clase `combinable`, vea [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `concrt-omp-fibonacci-reduction.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc/OpenMP concrt-OMP-Fibonacci-Reduction. cpp**

## <a name="see-also"></a>Consulte también

[Migración de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)
