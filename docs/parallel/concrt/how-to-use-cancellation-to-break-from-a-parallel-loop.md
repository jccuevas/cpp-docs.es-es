---
title: 'Cómo: usar la cancelación para interrumpir un bucle paralelo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1b5153c225c3bb3a67be4265cf8303da2121c2b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Cómo: Usar la cancelación para interrumpir un bucle Parallel
Este ejemplo muestra cómo se usa la cancelación para implementar un algoritmo de búsqueda paralelo básico.  
  
## <a name="example"></a>Ejemplo  

 En el ejemplo siguiente se usa la cancelación para buscar un elemento en una matriz. El `parallel_find_any` función utiliza la [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo y la [Concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) función para buscar la posición que contiene el valor dado. Cuando el bucle paralelo encuentra el valor, se llama a la [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) método para cancelar el trabajo posterior.  


  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  

 El [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo actúa de manera simultánea. Por lo tanto, no realiza las operaciones en un orden predeterminado. Si la matriz contiene varias instancias del valor, el resultado puede ser cualquiera de sus posiciones.  

  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-array-search.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc paralelo-matriz-search.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)   
 [cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)
