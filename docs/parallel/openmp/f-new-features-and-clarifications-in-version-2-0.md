---
title: "F. New Features and Clarifications in Version 2.0 | Microsoft Docs"
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
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# F. New Features and Clarifications in Version 2.0
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este apéndice resume los cambios clave realizados en la especificación de OpenMP C\/C\+\+ en mover la versión 1,0 a la versión 2,0.  los puntos siguientes son nuevas características agregadas a la especificación:  
  
-   las comas se permiten en las directivas de OpenMP \([sección 2,1](../../parallel/openmp/2-1-directive-format.md) en la página 7\).  
  
-   adición de la cláusula de `num_threads` .  Esta cláusula permite que un usuario solicite un número concreto de subprocesos para una construcción paralela \([sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8\).  
  
-   La directiva de `threadprivate` se ha mejorado para aceptar las variables estáticas de bloque\-ámbito \([sección 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) en la página 23\).  
  
-   Las matrices de longitud variable C99 son tipos completos, y se pueden especificar para cualquier parte completan tipos se permiten, como en las listas de `private`, de `firstprivate`, y las cláusulas de `lastprivate` \([sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25\).  
  
-   Una variable privada en una región paralela puede ser private marcado de nuevo en una directiva anidadas \([sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25\).  
  
-   se ha agregado la cláusula de `copyprivate` .  Proporciona un mecanismo para utilizar una variable privada para propagar un valor de un miembro de un equipo a los demás miembros.  Es una alternativa a utilizar una variable compartida por valor cuando proporcionar una variable tan compartida sería difícil \(por ejemplo, en una recursividad que requiere otra variable en cada nivel\).  La cláusula de `copyprivate` sólo puede aparecer en la directiva de **solo** \([sección 2.7.2.8](../Topic/2.7.2.8%20copyprivate.md) en la página 32\).  
  
-   Adición de rutinas `omp_get_wtick` y `omp_get_wtime` de tiempo similares a las rutinas de MPI.  Estas funciones son necesarias para realizar los controles de tiempo de reloj de muro \([sección 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) en la página 44 y [sección 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) en la página 45\).  
  
-   un apéndice con una lista de comportamientos implementación\-definido en OpenMP C\/C\+\+ se ha agregado.  Una implementación es necesario definir y documentar el comportamiento en estos casos \([apéndice E](../Topic/E.%20Implementation-Defined%20Behaviors%20in%20OpenMP%20C-C++.md) en la página 97\).  
  
-   Los cambios siguientes sirven clarificar o corregir características en la especificación anterior de OpenMP API para C\/C\+\+:  
  
    -   Se ha aclarado que el comportamiento de `omp_set_nested` y de `omp_set_dynamic` cuando `omp_in_parallel` devuelve cero es indefinido \([sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39, y [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40\).  
  
    -   Anidamiento de directivas aclarar cuándo se utiliza el paralelo anidadas \([sección 2,9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33\).  
  
    -   Las funciones de destrucción inicialización de bloqueo y de bloqueo se puede llamar en una región paralela \([sección 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) en la página 42 y [sección 3.2.2](../Topic/3.2.2%20omp_destroy_lock%20and%20omp_destroy_nest_lock%20Functions.md) en la página 42\).  
  
    -   Se han agregado nuevos ejemplos \([apéndice A](../Topic/A.%20Examples.md) en la página 51\).