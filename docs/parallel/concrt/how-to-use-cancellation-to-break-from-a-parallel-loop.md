---
title: 'Cómo: Usar la cancelación para interrumpir un bucle Parallel'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 2a19c2874ce331be2d4f5840f61cabf7bca9abf6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612750"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Cómo: Usar la cancelación para interrumpir un bucle Parallel

En este ejemplo se muestra cómo usar la cancelación para implementar un algoritmo de búsqueda paralelo básica.

## <a name="example"></a>Ejemplo

El ejemplo siguiente usa la cancelación para buscar un elemento en una matriz. El `parallel_find_any` función usa el [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo y la [Concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) función para buscar la posición que contiene el valor especificado. Cuando el bucle paralelo encuentra el valor, llama a la [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) método para cancelar el trabajo futuro.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

El [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo actúa de manera simultánea. Por lo tanto, no realiza las operaciones en un orden predeterminado. Si la matriz contiene varias instancias del valor, el resultado puede ser cualquiera de sus posiciones.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-array-search.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc paralelo-array-search.cpp**

## <a name="see-also"></a>Vea también

[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)
