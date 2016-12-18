---
title: "C&#243;mo: Convertir un bucle OpenMP que usa la cancelaci&#243;n para usar el runtime de simultaneidad | Microsoft Docs"
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
  - "convertir de OpenMP a Runtime de simultaneidad, cancelación"
  - "cancelación, convertir de OpenMP a Runtime de simultaneidad"
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir un bucle OpenMP que usa la cancelaci&#243;n para usar el runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Algunos bucles paralelos no necesitan que se ejecuten todas las iteraciones.  Por ejemplo, un algoritmo que busca un valor puede finalizar una vez que se encuentra el valor.  OpenMP no proporciona ningún mecanismo para interrumpir un bucle paralelo.  Sin embargo, puede usar un valor booleano, o marca, para permitir que una iteración del bucle indique que se ha encontrado la solución.  El runtime de simultaneidad proporciona funcionalidad que permite a una tarea cancelar otras tareas que todavía no se han iniciado.  
  
 En este ejemplo se muestra cómo convertir un bucle [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) de OpenMP que no necesita que se ejecuten todas las iteraciones para usar el mecanismo de cancelación del runtime de simultaneidad.  
  
## Ejemplo  
 En este ejemplo se usa OpenMP y el runtime de simultaneidad para implementar una versión paralela del algoritmo [std::any\_of](../Topic/any_of.md).  La versión de OpenMP de este ejemplo usa una marca para coordinar entre todas las iteraciones del bucle paralelo que se cumple la condición.  La versión que emplea el runtime de simultaneidad usa el método [concurrency::structured\_task\_group::cancel](../Topic/structured_task_group::cancel%20Method.md) para detener la operación global cuando se cumple la condición.  
  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Using OpenMP...**  
**9114046 is in the array.**  
**Using the Concurrency Runtime...**  
**9114046 is in the array.** En la versión que usa OpenMP, todas las iteraciones del bucle se ejecutan, incluso cuando se establece la marca.  Además, si una tarea fuera a tener tareas secundarias, la marca también tendría que estar disponible para que esas tareas secundarias comunicaran la cancelación.  En el runtime de simultaneidad, cuando se cancela un grupo de tareas, el runtime cancela todo el árbol de trabajo, incluidas las tareas secundarias.  El algoritmo [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) usa tareas para realizar el trabajo.  Por tanto, cuando una iteración del bucle cancela la tarea raíz, también se cancela todo el árbol de cálculo.  Cuando se cancela un árbol de trabajo, el runtime no inicia nuevas tareas.  Sin embargo, el runtime permite que las tareas que se han iniciado finalicen.  Por tanto, en el caso del algoritmo `parallel_for_each`, las iteraciones del bucle activas pueden limpiar sus recursos.  
  
 En ambas versiones de este ejemplo, si la matriz contiene más de una copia del valor que se va a buscar, varias iteraciones del bucle pueden establecer simultáneamente el resultado y cancelar la operación en su conjunto.  Puede usar una primitiva de sincronización, como una sección crítica, si el problema necesita que solo una tarea realice el trabajo cuando se cumple una condición.  
  
 También puede usar el control de excepciones para cancelar las tareas que usan la biblioteca PPL.  Para obtener más información sobre la cancelación, vea [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
 Para obtener más información sobre `parallel_for_each` y otros algoritmos paralelos, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `concrt-omp-parallel-any-of.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-parallel\-any\-of.cpp**  
  
## Vea también  
 [Migrar de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)