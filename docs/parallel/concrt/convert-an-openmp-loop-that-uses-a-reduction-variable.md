---
title: "C&#243;mo: Convertir un bucle OpenMP que usa una variable de reducci&#243;n para usar el Runtime de simultaneidad | Microsoft Docs"
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
  - "convertir de OpenMP a Runtime de simultaneidad, variables de reducción"
  - "variables de reducción, convertir de OpenMP a Runtime de simultaneidad"
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir un bucle OpenMP que usa una variable de reducci&#243;n para usar el Runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo convertir un bucle OpenMP [paralelo](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) que usa la cláusula [reduction](../../parallel/openmp/reference/reduction.md) para emplear el runtime de simultaneidad.  
  
 La cláusula OpenMP `reduction` permite especificar una o más variables privadas de subprocesos que están sujetas a una operación de reducción al final de la región paralela.  OpenMP predefine un conjunto de operadores de reducción.  Cada variable de reducción debe ser un escalar \(por ejemplo, `int`, `long` y `float`\).  OpenMP también define varias restricciones sobre cómo se usan las variables de reducción en una región paralela.  
  
 La biblioteca de patrones de procesamiento paralelo \(PPL\) proporciona la clase [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md), que proporciona un almacenamiento local de subprocesos reutilizable que permite realizar cálculos específicos y, a continuación, combinar estos cálculos en un resultado final.  La clase `combinable` es una plantilla que actúa en los tipos escalares y complejos.  Para usar la clase `combinable`, realice estos subcálculos en el cuerpo de una construcción paralela y, a continuación, llame al método [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) o [concurrency::combinable::combine\_each](../Topic/combinable::combine_each%20Method.md) para generar el resultado final.  Los métodos `combine` y `combine_each` toman una *función de combinación* que especifica cómo combinar cada par de elementos.  Por consiguiente, la clase `combinable` no se limita a un conjunto fijo de operadores de reducción.  
  
## Ejemplo  
 En este ejemplo se usa OpenMP y el runtime de simultaneidad para calcular la suma de los 35 primeros números de Fibonacci.  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Using OpenMP...**  
**The sum of the first 35 Fibonacci numbers is 14930351.**  
**Using the Concurrency Runtime...**  
**The sum of the first 35 Fibonacci numbers is 14930351.** Para obtener más información sobre la clase `combinable`, vea [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `concrt-omp-fibonacci-reduction.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-fibonacci\-reduction.cpp**  
  
## Vea también  
 [Migrar de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)