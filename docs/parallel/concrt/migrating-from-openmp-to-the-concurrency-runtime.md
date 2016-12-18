---
title: "Migrar de OpenMP al Runtime de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Runtime de simultaneidad, migrar desde OpenMP"
  - "OpenMP, migrar al Runtime de simultaneidad"
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
caps.latest.revision: 12
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Migrar de OpenMP al Runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Runtime de simultaneidad habilita diversos modelos de programación.  Estos modelos pueden superponerse a los modelos de otras bibliotecas o complementarlos.  En los documentos de esta sección se compara [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md) con el runtime de simultaneidad y se proporcionan ejemplos sobre cómo migrar el código existente de OpenMP para usar el runtime de simultaneidad.  
  
 El modelo de programación OpenMP se define como un estándar abierto y está claramente enlazado a los lenguajes de programación Fortran y C\/C\+\+.  Las versiones 2.0 y 2.5 de OpenMP, admitidas por el compilador de Visual C\+\+, son particularmente adecuadas para los algoritmos paralelos que son iterativos; es decir, que realizan la iteración paralela sobre una matriz de datos.  OpenMP 3.0 admite las tareas no iterativas, además de las tareas iterativas.  
  
 OpenMP es más eficaz cuando el grado de paralelismo está predeterminado y coincide con los recursos disponibles en el sistema.  El modelo OpenMP se presta especialmente para la computación de alto rendimiento, en la que se distribuyen problemas de computación muy grandes entre los recursos de procesamiento de un equipo.  En este escenario, el entorno de hardware suele ser fijo y el desarrollador puede esperar obtener acceso exclusivo a todos los recursos de computación cuando se ejecuta el algoritmo.  
  
 Sin embargo, los entornos de computación menos restringidos pueden no ser apropiados para OpenMP.  Por ejemplo, los problemas recursivos, como el algoritmo de ordenación rápida \(quicksort\) o las búsquedas en un árbol de datos, son más difíciles de implementar mediante OpenMP 2.0 y 2.5.  El runtime de simultaneidad complementa las capacidades de OpenMP, ya que proporciona la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) y la [biblioteca de modelos de procesamiento paralelo](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\).  La biblioteca de agentes asincrónicos admite el paralelismo de tareas generales; PPL admite tareas paralelas más específicas.  El runtime de simultaneidad proporciona la infraestructura necesaria para realizar operaciones en paralelo, de modo que se pueda centrar en la lógica de la aplicación.  Sin embargo, como el runtime de simultaneidad habilita diversos modelos de programación, la sobrecarga de programación puede ser mayor que otras bibliotecas de simultaneidad como OpenMP.  Por tanto, se recomienda que pruebe el rendimiento de forma incremental cuando convierta el código existente de OpenMP para usar el runtime de simultaneidad.  
  
## Cuándo migrar OpenMP al runtime de simultaneidad  
 Puede ser ventajoso migrar el código existente de OpenMP para usar el runtime de simultaneidad en los casos siguientes.  
  
|Casos|Ventajas del runtime de simultaneidad|  
|-----------|-------------------------------------------|  
|Se requiere un marco extensible de programación simultánea.|Muchas de las características del Runtime de simultaneidad se pueden extender.  Además, se pueden combinar las características existentes para crear nuevas características.  Dado que OpenMP se basa en las directivas del compilador, no se puede extender con facilidad.|  
|La aplicación se beneficiaría del bloqueo cooperativo.|Cuando se bloquea una tarea porque requiere un recurso que no está disponible todavía, el runtime de simultaneidad pueden realizar otras tareas mientras la primera tarea espera el recurso.|  
|La aplicación se beneficiaría del equilibrio de carga dinámico.|El runtime de simultaneidad usa un algoritmo de programación que ajusta la asignación de los recursos de computación a medida que cambian las cargas de trabajo.  En OpenMP, cuando el programador asigna a los recursos de computación a una región paralela, esas asignaciones de recursos se corrigen en el cálculo.|  
|Se requiere la compatibilidad con el control de excepciones.|PPL permite detectar las excepciones tanto dentro como fuera de una región o un bucle en paralelo.  En OpenMP, debe controlar la excepción en la región o el bucle en paralelo.|  
|Necesita un mecanismo de cancelación.|PPL permite a las aplicaciones cancelar las tareas individuales y los árboles de trabajo paralelos.  OpenMP requiere la aplicación para implementar su propio mecanismo de cancelación.|  
|Se requiere que el código paralelo finalice en un contexto diferente de aquel en el que comienza.|El runtime de simultaneidad permite iniciar una tarea en un contexto y, a continuación, esperar o cancelar esa tarea en otro contexto.  En OpenMP, todo el trabajo paralelo debe finalizar en el contexto en el que comienza.|  
|Requiere la compatibilidad con la depuración mejorada.|Visual Studio proporciona las ventanas **Pilas paralelas** y **Tareas paralelas** para que se puedan depurar más fácilmente las aplicaciones multiproceso.<br /><br /> Para obtener más información sobre la compatibilidad con la depuración para el runtime de simultaneidad, vea [Usar la ventana Tareas](../Topic/Using%20the%20Tasks%20Window.md), [Uso de la ventana Tareas paralelas](../Topic/Using%20the%20Parallel%20Stacks%20Window.md) y [Tutorial: Depurar una aplicación paralela](../Topic/Walkthrough:%20Debugging%20a%20Parallel%20Application.md).|  
  
## Cuándo no migrar OpenMP al runtime de simultaneidad  
 En los casos siguientes se describe cuándo no sería adecuado migrar el código existente de OpenMP para usar el runtime de simultaneidad.  
  
|Casos|Explicación|  
|-----------|-----------------|  
|La aplicación ya cumple los requisitos.|Si está de acuerdo con el rendimiento de la aplicación y la compatibilidad actual con la depuración, la migración podría no ser adecuada.|  
|Los cuerpos de bucles paralelos realizan poco trabajo.|La sobrecarga del programador de tareas del runtime de simultaneidad no puede superar las ventajas de ejecutar el cuerpo del bucle en paralelo, sobre todo cuando el cuerpo del bucle es relativamente pequeño.|  
|La aplicación está escrita en C.|Dado que el runtime de simultaneidad usa muchas características de C\+\+, podría no resultar práctico cuando no se puede escribir código que permita a la aplicación C usarlo por completo.|  
  
## Temas relacionados  
 [Cómo: Convertir un bucle OpenMP paralelo para usar el runtime de simultaneidad](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  
 Dado un bucle básico que usa el OpenMP [paralelo](../../parallel/openmp/reference/parallel.md) y las directivas de [para](../../parallel/openmp/reference/for-openmp.md) , muestra cómo convertirlo para usar el algoritmo de [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) del runtime de simultaneidad.  
  
 [Cómo: Convertir un bucle OpenMP que usa la cancelación para usar el runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 Dado un bucle de OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) que no requiere que se ejecuten todas las iteraciones, muestra cómo convertirlo para usar el mecanismo de cancelación del runtime de simultaneidad.  
  
 [Cómo: Convertir un bucle OpenMP que usa el control de excepciones para usar el runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 Dado un bucle de OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) que realiza el control de excepciones, muestra cómo convertirlo para usar el mecanismo de control de excepciones del runtime de simultaneidad.  
  
 [Cómo: Convertir un bucle OpenMP que usa una variable de reducción para usar el Runtime de simultaneidad](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 Dado un bucle de OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) que usa la cláusula [reduction](../../parallel/openmp/reference/reduction.md), muestra cómo convertirlo para usar el runtime de simultaneidad.  
  
## Vea también  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)