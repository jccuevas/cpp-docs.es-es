---
title: "F. Nuevas características y aclaraciones en la versión 2.0 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9a661f183816fec0f7a71c990f1508338100f4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nuevas características y aclaraciones en la versión 2.0
Este apéndice resume los cambios claves realizados en la especificación de OpenMP C/C++ de cambio de la versión 1.0 a la versión 2.0. Los elementos siguientes son nuevas características agregadas a la especificación de:  
  
-   Se permiten comas en directivas de OpenMP ([sección 2.1](../../parallel/openmp/2-1-directive-format.md) en la página 7).  
  
-   Adición de la `num_threads` cláusula. Esta cláusula permite al usuario solicitar un número específico de subprocesos de una construcción paralela ([sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8).  
  
-   El `threadprivate` directiva se ha ampliado para que acepte las variables de ámbito de bloque estático ([punto 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) en la página 23).  
  
-   Las matrices de longitud Variable C99 son tipos completos y, por tanto, se pueden especificar en cualquier parte se permiten tipos completos, por ejemplo en las listas de `private`, `firstprivate`, y `lastprivate` cláusulas ([sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25).  
  
-   Una variable privada en una región paralela puede marcarse como privada en una directiva anidada ([sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en página 25).  
  
-   El `copyprivate` se ha agregado la cláusula. Proporciona un mecanismo para utilizar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor al proporcionar esa variable compartida sería difícil (por ejemplo, en una necesidad de una variable distinta en cada nivel de recursividad). El `copyprivate` cláusula solamente puede aparecer en el **único** directiva ([sección 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) en la página 32).  
  
-   Adición de rutinas de control de tiempo `omp_get_wtick` y `omp_get_wtime` similares a las rutinas MPI. Estas funciones son necesarias para realizar la frecuencia de reloj de pared ([sección 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) en la página 44 y [sección 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) en página 45).  
  
-   Se ha agregado un apéndice con una lista de comportamientos definido por la implementación de OpenMP C o C++. Una implementación es necesaria para definir y documentar su comportamiento en estos casos ([Apéndice E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) en página 97).  
  
-   Los cambios siguientes sirven para aclarar o corregir características en la especificación de API de OpenMP anterior para C y C++:  
  
    -   Se ha aclarado que el comportamiento de `omp_set_nested` y `omp_set_dynamic` cuando `omp_in_parallel` devuelve es distinto de cero no está definido ([sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39, y [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40).  
  
    -   Se ha aclarado el anidamiento de directivas cuando se usa paralelo anidada ([sección 2.9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33).  
  
    -   Pueden llamar a las funciones de destrucción de inicialización y bloqueo de bloqueo en una región paralela ([sección 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) en la página 42 y [punto 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) en la página 42).  
  
    -   Se han agregado nuevos ejemplos ([Apéndice A](../../parallel/openmp/a-examples.md) en página 51).