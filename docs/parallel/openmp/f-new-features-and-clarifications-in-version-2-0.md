---
title: F. Las nuevas características y aclaraciones de la versión 2.0
ms.date: 11/04/2016
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: c8a597c6af397bd162d92a945d96409b1839e2a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657159"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Las nuevas características y aclaraciones de la versión 2.0

En este apéndice se resume los cambios clave que se realizan en la especificación OpenMP C/C ++ en pasar de la versión 1.0 a la versión 2.0. Los elementos siguientes son las nuevas características agregadas a la especificación de:

- Se permiten comas en directivas de OpenMP ([sección 2.1](../../parallel/openmp/2-1-directive-format.md) en la página 7).

- Adición de la `num_threads` cláusula. Esta cláusula permite que un usuario solicitar un número específico de subprocesos para una construcción paralela ([sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8).

- El `threadprivate` directiva se ha ampliado para que acepte las variables de ámbito de bloque estático ([punto 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) en la página 23).

- Matrices de longitud Variable C99 son tipos completos y, por tanto, pueden especificarse en cualquier parte se permiten tipos completos, por ejemplo en las listas de `private`, `firstprivate`, y `lastprivate` cláusulas ([sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25).

- Una variable privada en una región paralela puede marcarse como privada a intentarlo dentro de una directiva anidada ([sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25).

- El `copyprivate` cláusula se ha agregado. Proporciona un mecanismo para usar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor al que proporciona este tipo de variable compartida puede ser difícil (por ejemplo, en una necesidad de una variable diferente en cada nivel de recursividad). El `copyprivate` cláusula solamente puede aparecer en el **único** directiva ([sección 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) en la página 32).

- Adición de rutinas de control de tiempo `omp_get_wtick` y `omp_get_wtime` similares a las rutinas MPI. Estas funciones son necesarias para realizar la frecuencia de reloj de pared ([sección 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) en la página 44 y [sección 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) en página 45).

- Se ha agregado un apéndice con una lista de comportamientos definido por la implementación de OpenMP C/C ++. Una implementación es necesaria para definir y documentar su comportamiento en estos casos ([Apéndice E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) en página 97).

- Los cambios siguientes sirven para aclarar o corregir las características de la especificación de API de OpenMP anterior para C/C ++:

   - Se ha aclarado que el comportamiento de `omp_set_nested` y `omp_set_dynamic` cuando `omp_in_parallel` devuelve distinto de cero no está definido ([sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39, y [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40).

   - Se ha aclarado el anidamiento de directivas cuando se usa paralelo anidada ([sección 2.9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33).

   - Las funciones de destrucción de inicialización y el bloqueo de bloqueo se pueden llamar en una región paralela ([sección 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) en la página 42 y [sección 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) en la página 42).

   - Se han agregado nuevos ejemplos ([Apéndice A](../../parallel/openmp/a-examples.md) en página 51).