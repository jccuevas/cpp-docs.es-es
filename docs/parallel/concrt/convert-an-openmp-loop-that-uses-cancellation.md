---
title: 'Cómo: Convertir un bucle OpenMP que usa la cancelación para usar el runtime de simultaneidad'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: f4d4d8d1b2dbf60d0b4674229043c981d874292d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141822"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Cómo: Convertir un bucle OpenMP que usa la cancelación para usar el runtime de simultaneidad

Algunos bucles paralelos no necesitan que se ejecuten todas las iteraciones. Por ejemplo, un algoritmo que busca un valor puede finalizar una vez que se encuentra el valor. OpenMP no proporciona ningún mecanismo para interrumpir un bucle paralelo. Sin embargo, puede usar un valor booleano, o marca, para permitir que una iteración del bucle indique que se ha encontrado la solución. El runtime de simultaneidad proporciona funcionalidad que permite a una tarea cancelar otras tareas que todavía no se han iniciado.

En este ejemplo se muestra cómo convertir un bucle[for de](../../parallel/openmp/reference/for-openmp.md) OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)for que no requiere que todas las iteraciones se ejecuten para utilizar el mecanismo de cancelación de Runtime de simultaneidad.

## <a name="example"></a>Ejemplo

En este ejemplo se usa OpenMP y el Runtime de simultaneidad para implementar una versión paralela del algoritmo [STD:: any_of](../../standard-library/algorithm-functions.md#any_of) . La versión de OpenMP de este ejemplo usa una marca para coordinar entre todas las iteraciones del bucle paralelo que se cumple la condición. La versión que usa el Runtime de simultaneidad usa el método [Concurrency:: structured_task_group:: CANCEL](reference/structured-task-group-class.md#cancel) para detener la operación global cuando se cumple la condición.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

En la versión que usa OpenMP, todas las iteraciones del bucle se ejecutan, incluso cuando se establece la marca. Además, si una tarea fuera a tener tareas secundarias, la marca también tendría que estar disponible para que esas tareas secundarias comunicaran la cancelación. En el Runtime de simultaneidad, cuando se cancela un grupo de tareas, el tiempo de ejecución cancela todo el árbol de trabajo, incluidas las tareas secundarias. El algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) usa tareas para realizar el trabajo. Por lo tanto, cuando una iteración del bucle cancela la tarea raíz, también se cancela todo el árbol de cálculo. Cuando se cancela un árbol de trabajo, el tiempo de ejecución no inicia nuevas tareas. Sin embargo, el runtime permite que las tareas que se han iniciado finalicen. Por tanto, en el caso del algoritmo `parallel_for_each`, las iteraciones del bucle activas pueden limpiar sus recursos.

En ambas versiones de este ejemplo, si la matriz contiene más de una copia del valor que se va a buscar, varias iteraciones del bucle pueden establecer simultáneamente el resultado y cancelar la operación en su conjunto. Puede usar una primitiva de sincronización, como una sección crítica, si el problema necesita que solo una tarea realice el trabajo cuando se cumple una condición.

También puede usar el control de excepciones para cancelar las tareas que usan la biblioteca PPL. Para obtener más información sobre la cancelación, vea [cancelación en la biblioteca PPL](cancellation-in-the-ppl.md).

Para obtener más información sobre `parallel_for_each` y otros algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `concrt-omp-parallel-any-of.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc/OpenMP concrt-OMP-Parallel-any-of. cpp**

## <a name="see-also"></a>Consulte también

[Migración de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)
