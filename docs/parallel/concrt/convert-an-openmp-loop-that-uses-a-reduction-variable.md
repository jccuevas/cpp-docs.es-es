---
title: Procedimiento Convertir un bucle OpenMP que usa una Variable de reducción para usar el Runtime de simultaneidad
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: d75e115bdb1d13c9e8f45ed67d0f3993eac1b387
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413962"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Procedimiento Convertir un bucle OpenMP que usa una Variable de reducción para usar el Runtime de simultaneidad

En este ejemplo se muestra cómo convertir de OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que usa el [reducción](../../parallel/openmp/reference/reduction.md) cláusula para usar el Runtime de simultaneidad.

La cláusula OpenMP `reduction` permite especificar una o más variables privadas de subprocesos que están sujetas a una operación de reducción al final de la región paralela. OpenMP predefine un conjunto de operadores de reducción. Cada variable de reducción debe ser un escalar (por ejemplo, `int`, `long` y `float`). OpenMP también define varias restricciones sobre cómo se usan las variables de reducción en una región paralela.

La biblioteca de patrones paralelos (PPL) proporciona la [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) (clase), que proporciona almacenamiento local de subprocesos reutilizable que permite realizar cálculos específicos y, a continuación, fusionar mediante combinación estos cálculos en un final resultado. La clase `combinable` es una plantilla que actúa en los tipos escalares y complejos. Para usar el `combinable` clase, realice estos subcálculos en el cuerpo de una construcción paralela y, a continuación, llamar a la [concurrency::combinable::combine](reference/combinable-class.md#combine) o [combine_each](reference/combinable-class.md#combine_each) método para generar el resultado final. El `combine` y `combine_each` métodos aceptan un *combinar la función* que especifica cómo combinar cada par de elementos. Por consiguiente, la clase `combinable` no se limita a un conjunto fijo de operadores de reducción.

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

Para obtener más información sobre la `combinable` de clases, vea [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `concrt-omp-fibonacci-reduction.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc/OpenMP concrt-omp-fibonacci-reduction.cpp**

## <a name="see-also"></a>Vea también

[Migración de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)
