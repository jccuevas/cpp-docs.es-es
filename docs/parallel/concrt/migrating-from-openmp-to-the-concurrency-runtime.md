---
title: Migrar de OpenMP al Runtime de simultaneidad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65359e76e036a0d8d33de2de9f6c96c6425d2152
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrar de OpenMP al Runtime de simultaneidad
El Runtime de simultaneidad ofrece una variedad de modelos de programación. Estos modelos pueden superponerse o complementar los modelos de otras bibliotecas. Los documentos en esta sección compare [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) al Runtime de simultaneidad y se proporcionan ejemplos sobre cómo migrar código existente de OpenMP para usar el Runtime de simultaneidad.  
  
 El modelo de programación de OpenMP se define con un estándar abierto y tiene enlaces bien definidos con los lenguajes de programación Fortran y C/C++. Las versiones de OpenMP 2.0 y 2.5, que son compatibles con el compilador de Visual C++, son adecuadas para los algoritmos paralelos que son iterativos; es decir, realizan la iteración paralela a través de una matriz de datos. OpenMP 3.0 admite no iterativo tareas además de las tareas iterativas.  
  
 OpenMP es más eficaz cuando el grado de paralelismo se determina previamente y coincide con los recursos disponibles en el sistema. El modelo de OpenMP es un especialmente apropiada para informática de alto rendimiento, que se distribuyen los problemas de cálculo muy grandes a través de los recursos de procesamiento de un equipo. En este escenario, el entorno de hardware generalmente es fijo y el desarrollador puede esperar tener acceso exclusivo a todos los recursos informáticos cuando se ejecuta el algoritmo.  
  
 Sin embargo, menos restringidos entornos informáticos puede ser apropiada para OpenMP. Por ejemplo, problemas de recursiva (por ejemplo, el algoritmo quicksort o buscar un árbol de datos) son más difíciles de implementar mediante OpenMP 2.0 y 2.5. El Runtime de simultaneidad complementa las capacidades de OpenMP proporcionando la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) y [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). La biblioteca de agentes asincrónicos admite el paralelismo de grano grueso tarea; la biblioteca PPL admite más tareas paralelas específicas. El Runtime de simultaneidad proporciona la infraestructura necesaria para realizar operaciones en paralelo para que pueda centrarse en la lógica de la aplicación. Sin embargo, dado que el Runtime de simultaneidad permite una variedad de modelos de programación, la sobrecarga de programación puede ser mayor que otras bibliotecas de simultaneidad como OpenMP. Por lo tanto, se recomienda probar rendimiento de forma incremental al convertir el código existente de OpenMP para usar el Runtime de simultaneidad.  
  
## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Cuándo se debe migrar de OpenMP al Runtime de simultaneidad  
 Puede ser conveniente para migrar el código existente de OpenMP para usar el Runtime de simultaneidad en los casos siguientes.  
  
|Cases|Ventajas del Runtime de simultaneidad|  
|-----------|-------------------------------------------|  
|Necesita un marco de programación simultáneo extensible.|Muchas de las características del Runtime de simultaneidad se pueden extender. También puede combinar características existentes para crear nuevas características. Dado que OpenMP se basa en las directivas de compilador, se no se puede ampliar fácilmente.|  
|La aplicación se beneficiaría de bloqueo cooperativo.|Cuando una tarea se bloquea porque requiere un recurso que aún no está disponible, el Runtime de simultaneidad puede realizar otras tareas mientras espera a que la primera tarea para el recurso.|  
|La aplicación se beneficiaría de equilibrio dinámico de carga.|El Runtime de simultaneidad usa un algoritmo de programación que ajusta la asignación de recursos de computación a medida que cambian las cargas de trabajo. En OpenMP, cuando el programador asigna recursos informáticos para una región paralela, estas asignaciones de recursos son fijos en el cálculo.|  
|Necesita compatibilidad con el control de excepciones.|La biblioteca PPL permite detectar excepciones tanto dentro como fuera de un bucle o una región paralela. En OpenMP, debe controlar la excepción dentro de la región paralela o bucle.|  
|Requieren un mecanismo de cancelación.|La biblioteca PPL permite que las aplicaciones cancelar tareas individuales y paralelo árboles de trabajo. OpenMP requiere que la aplicación para implementar su propio mecanismo de cancelación.|  
|Requerir código paralelo en un contexto diferente del que se inició.|El Runtime de simultaneidad le permite iniciar una tarea en un contexto y, a continuación, esperar o cancelar la tarea en otro contexto. En OpenMP, debe finalizar todo el trabajo paralelo en el contexto desde el que se inicia.|  
|Necesita compatibilidad con la depuración mejorada.|Visual Studio proporciona el **pilas paralelas** y **tareas paralelas** windows para que puedan depurar más fácilmente aplicaciones multiproceso.<br /><br /> Para obtener más información acerca de la compatibilidad de depuración para el Runtime de simultaneidad, vea [mediante la ventana tareas](/visualstudio/debugger/using-the-tasks-window), [mediante la ventana Pilas paralelas](/visualstudio/debugger/using-the-parallel-stacks-window), y [Tutorial: depurar un paralelo Aplicación](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|  
  
## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Cuándo no se deben migrar de OpenMP al Runtime de simultaneidad  
 Los casos siguientes se describen los que quizás no sea adecuado para migrar el código existente de OpenMP para usar el Runtime de simultaneidad.  
  
|Cases|Explicación|  
|-----------|-----------------|  
|La aplicación ya cumple los requisitos.|Si está satisfecho con el rendimiento de la aplicación y soporte técnico de depuración actual, migración podría no ser adecuado.|  
|Los cuerpos de bucle paralelo realizan poco trabajo.|La sobrecarga que supone el programador de tareas del Runtime de simultaneidad no puede superar las ventajas de ejecutar el cuerpo del bucle en paralelo, sobre todo cuando el cuerpo del bucle es relativamente pequeño.|  
|La aplicación está escrita en C.|Dado que el Runtime de simultaneidad usa muchas características de C++, podrían no ser adecuado cuando no se puede escribir código que permite a la aplicación de C totalmente usarlo.|  
  
## <a name="related-topics"></a>Temas relacionados  
 [Procedimiento para convertir un bucle OpenMP paralelo para usar el Runtime de simultaneidad](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  

 Dado un bucle básico que usa el OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) y [para](../../parallel/openmp/reference/for-openmp.md) directivas, se muestra cómo convertir para usar el Runtime de simultaneidad [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo.  

  
 [Procedimiento para convertir un bucle OpenMP que usa la cancelación para usar el Runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 Dado un OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que no requiera todas las iteraciones que se ejecuta, se muestra cómo convertir para que utilice el mecanismo de cancelación del Runtime de simultaneidad.  
  
 [Procedimiento para convertir un bucle OpenMP que usa el control de excepciones para usar el Runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 Dado un OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que realiza el control de excepciones, se muestra cómo convertir para utilizar el mecanismo de control de excepciones de Runtime de simultaneidad.  
  
 [Procedimiento para convertir un bucle OpenMP que usa una variable de reducción para usar el Runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 Dado un OpenMP [paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[para](../../parallel/openmp/reference/for-openmp.md) bucle que usa el [reducción](../../parallel/openmp/reference/reduction.md) cláusula, se muestra cómo convertir para usar el Runtime de simultaneidad.  
  
## <a name="see-also"></a>Vea también  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)   
 [Biblioteca de modelos de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)

