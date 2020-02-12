---
title: 'Cómo: Usar la cancelación para interrumpir un bucle Parallel'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142134"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Cómo: Usar la cancelación para interrumpir un bucle Parallel

En este ejemplo se muestra cómo usar la cancelación para implementar un algoritmo básico de búsqueda en paralelo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa la cancelación para buscar un elemento en una matriz. La función `parallel_find_any` usa el algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) y la función [Concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) para buscar la posición que contiene el valor especificado. Cuando el bucle paralelo encuentra el valor, llama al método [Concurrency:: cancellation_token_source:: CANCEL](reference/cancellation-token-source-class.md#cancel) para cancelar el trabajo futuro.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

El algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) actúa simultáneamente. Por lo tanto, no realiza las operaciones en un orden determinado previamente. Si la matriz contiene varias instancias del valor, el resultado puede ser cualquiera de sus posiciones.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-array-search.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Parallel-array-Search. cpp**

## <a name="see-also"></a>Consulte también

[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for función)](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)
