---
title: F. Las nuevas características y aclaraciones de la versión 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362719"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Las nuevas características y aclaraciones de la versión 2.0

En este apéndice se resume los cambios clave que se realizan en la especificación OpenMP C/C ++ en pasar de la versión 1.0 a la versión 2.0. Los elementos siguientes son las nuevas características agregadas a la especificación de:

- Se permiten comas en OpenMP [directivas](2-directives.md#21-directive-format).

- Adición de la `num_threads` cláusula. Esta cláusula permite que un usuario solicitar un número específico de subprocesos para un [construcción paralela](2-directives.md#23-parallel-construct).

- El [threadprivate](2-directives.md#271-threadprivate-directive) directiva se ha ampliado para que acepte las variables de ámbito de bloque estático.

- Matrices de longitud Variable C99 son tipos completos y pueden especificarse en cualquier lugar tipos completos están permitidos, como en las listas de `private`, `firstprivate`, y `lastprivate` cláusulas (consulte [sección 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Se puede marcar una variable privada en una región paralela [privada](2-directives.md#2721-private) nuevo en una directiva anidada.

- El `copyprivate` cláusula se ha agregado. Proporciona un mecanismo para usar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor al que proporciona este tipo de variable compartida puede ser difícil (por ejemplo, en una necesidad de una variable diferente en cada nivel de recursividad). El [copyprivate](2-directives.md#2728-copyprivate) cláusula solamente puede aparecer en el `single` directiva.

- Adición de rutinas de control de tiempo [omp_get_wtick ()](3-run-time-library-functions.md#332-omp_get_wtick-function) y [omp_get_wtime ()](3-run-time-library-functions.md#331-omp_get_wtime-function) similares a las rutinas MPI. Estas funciones son necesarias para la frecuencia de reloj de pared.

- Un apéndice con una lista de [comportamientos definidos por implementación](e-implementation-defined-behaviors-in-openmp-c-cpp.md) en OpenMP C/C ++ que se ha agregado. Una implementación es necesaria para definir y documentar su comportamiento en estos casos.

- Los cambios siguientes sirven para aclarar o corregir las características de la especificación de API de OpenMP anterior para C/C ++:

  - Se ha aclarado que el comportamiento de [omp_set_nested ()](3-run-time-library-functions.md#319-omp_set_nested-function) y [omp_set_dynamic ()](3-run-time-library-functions.md#317-omp_set_dynamic-function) cuando `omp_in_parallel` devuelve distinto de cero es indefinido.

  - Se ha aclarado [anidamiento de directivas](2-directives.md#29-directive-nesting) cuando se usa paralelo anidado.

  - El [bloquear inicialización](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) y [bloquear destrucción](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) las funciones se pueden llamar en una región paralela.

  - Se agregaron nuevos ejemplos a [Apéndice A](a-examples.md).