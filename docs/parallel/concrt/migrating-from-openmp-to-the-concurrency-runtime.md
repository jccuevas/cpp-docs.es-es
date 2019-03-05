---
title: Migrar de OpenMP al Runtime de simultaneidad
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 16b0f175867e18e127997749098cce998674b3d2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259508"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrar de OpenMP al Runtime de simultaneidad

El Runtime de simultaneidad ofrece una variedad de modelos de programación. Estos modelos pueden superponerse o complementar los modelos de otras bibliotecas. Los documentos en esta sección comparar [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) al Runtime de simultaneidad y se proporcionan ejemplos sobre cómo migrar código existente de OpenMP para usar el Runtime de simultaneidad.

El modelo de programación de OpenMP se define con un estándar abierto y tiene enlaces bien definidos con los lenguajes de programación Fortran y C/C++. Las versiones 2.0 y 2.5, que son compatibles con el compilador de Visual C++, OpenMP son adecuadas para los algoritmos paralelos que son iterativos; es decir, realizan la iteración paralela a través de una matriz de datos. OpenMP 3.0 admite tareas que no son iterativas además de las tareas iterativas.

OpenMP es más eficaz cuando el grado de paralelismo se determina previamente y coincide con los recursos disponibles en el sistema. El modelo de OpenMP es una coincidencia de métodos especialmente adecuados para informática de alto rendimiento, que se distribuyen los problemas de cálculo muy grandes a través de los recursos de procesamiento de un equipo. En este escenario, el entorno de hardware generalmente es fijo y el desarrollador puede esperar a tener acceso exclusivo a todos los recursos informáticos cuando se ejecuta el algoritmo.

Sin embargo, menos entornos informáticos restringidos puede no ser apropiada para OpenMP. Por ejemplo, los problemas recursivos (como el algoritmo quicksort o búsqueda de un árbol de datos) son más difíciles de implementar con OpenMP 2.0 y 2.5. El Runtime de simultaneidad complementa la funcionalidad de OpenMP proporcionando la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) y [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). La biblioteca de agentes asincrónicos admite paralelismo de tareas generales; la biblioteca PPL admite más tareas paralelas específicas. El Runtime de simultaneidad proporciona la infraestructura necesaria para realizar operaciones en paralelo para que pueda centrarse en la lógica de la aplicación. Sin embargo, dado que el Runtime de simultaneidad permite una variedad de modelos de programación, su sobrecarga de programación puede ser mayor que otras bibliotecas de simultaneidad como OpenMP. Por lo tanto, se recomienda probar incrementalmente de rendimiento, al convertir el código existente de OpenMP para usar el Runtime de simultaneidad.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Cuándo realizar la migración de OpenMP a Runtime de simultaneidad

Puede ser conveniente para migrar código existente de OpenMP para usar el Runtime de simultaneidad en los casos siguientes.

|Cases|Ventajas del Runtime de simultaneidad|
|-----------|-------------------------------------------|
|Requieren un marco de programación simultáneo extensible.|Muchas de las características del Runtime de simultaneidad se pueden extender. También puede combinar características existentes para crear nuevas características. Dado que OpenMP se basa en las directivas de compilador, no puede ampliarse fácilmente.|
|La aplicación se beneficiaría de bloqueo cooperativo.|Cuando una tarea se bloquea porque requiere un recurso que aún no está disponible, el Runtime de simultaneidad puede realizar otras tareas mientras la primera tarea espera a que el recurso.|
|La aplicación se beneficiaría de equilibrio de carga dinámico.|El Runtime de simultaneidad usa un algoritmo de programación que ajusta la asignación de los recursos informáticos a medida que cambian las cargas de trabajo. En OpenMP, cuando el programador asigna recursos informáticos para una región paralela, esas asignaciones de recursos son fijas en todo el cálculo.|
|Requerir compatibilidad con el control de excepciones.|La biblioteca PPL permite detectar las excepciones tanto dentro como fuera de un bucle o una región paralela. En OpenMP, debe controlar la excepción dentro de la región paralela o un bucle.|
|Requieren un mecanismo de cancelación.|La biblioteca PPL permite a las aplicaciones cancelar tareas individuales y paralelo árboles de trabajo. OpenMP requiere que la aplicación para implementar su propio mecanismo de cancelación.|
|Requerir código paralelo para finalizar en un contexto diferente del que se inicia.|El Runtime de simultaneidad permite iniciar una tarea en un contexto y, a continuación, esperar o cancelar la tarea en otro contexto. En OpenMP, todo el trabajo paralelo debe finalizar en el contexto desde el que se inicia.|
|Requerir compatibilidad mejorada con la depuración.|Visual Studio proporciona la **pilas paralelas** y **tareas paralelas** windows para que pueda depurar más fácilmente aplicaciones multiproceso.<br /><br /> Para obtener más información sobre la compatibilidad de depuración para el Runtime de simultaneidad, consulte [mediante la ventana tareas](/visualstudio/debugger/using-the-tasks-window), [mediante la ventana Pilas paralelas](/visualstudio/debugger/using-the-parallel-stacks-window), y [Tutorial: Depurar una aplicación paralela](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Cuándo no se debe migrar de OpenMP a Runtime de simultaneidad

Los casos siguientes describen quizás no sea adecuado para migrar código existente de OpenMP para usar el Runtime de simultaneidad.

|Cases|Explicación|
|-----------|-----------------|
|La aplicación ya cumple sus requisitos.|Si está satisfecho con el rendimiento de la aplicación y la compatibilidad de depuración actual, migración podría no ser adecuada.|
|Los cuerpos de bucle paralelo realizan poco trabajo.|La sobrecarga del programador de tareas Runtime de simultaneidad no puede superar las ventajas de ejecutar el cuerpo del bucle en paralelo, especialmente cuando el cuerpo del bucle es relativamente pequeño.|
|La aplicación se escribe en C.|Dado que el Runtime de simultaneidad usa muchas características de C++, podría no ser adecuado cuando no se puede escribir código que permite que la aplicación de C se usa por completo.|

## <a name="related-topics"></a>Temas relacionados

[Cómo: Convertir un bucle OpenMP paralelo para usar el runtime de simultaneidad](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

Dado un bucle básico que usa el OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) y [para](../../parallel/openmp/reference/for-openmp.md) directivas, se muestra cómo convertir para que use el Runtime de simultaneidad [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo.

[Cómo: Convertir un bucle OpenMP que usa la cancelación para usar el runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
Dado un OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que no requiere que todas las iteraciones que se ejecutan, se muestra cómo convertir para que use el mecanismo de cancelación del Runtime de simultaneidad.

[Cómo: Convertir un bucle OpenMP que usa el control de excepciones para usar el runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
Dado un OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que realiza el control de excepciones, se muestra cómo convertir para que use el mecanismo de control de excepciones de Runtime de simultaneidad.

[Cómo: Convertir un bucle OpenMP que usa una variable de reducción para usar el Runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
Dado un OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que usa el [reducción](../../parallel/openmp/reference/reduction.md) cláusula, se muestra cómo convertir para que use el Runtime de simultaneidad.

## <a name="see-also"></a>Vea también

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)
