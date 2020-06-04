---
title: F. Nuevas características y aclaraciones de la versión 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 8cd82000992ab957bf2c41f11deccd65e2e6ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215038"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nuevas características y aclaraciones de la versión 2.0

En este apéndice se resumen los cambios clave realizados en la especificación CC++ /de OpenMP en pasar de la versión 1,0 a la versión 2,0. Los elementos siguientes son nuevas características que se han agregado a la especificación:

- Se permiten comas en las [directivas](2-directives.md#21-directive-format)de OpenMP.

- Adición de la cláusula `num_threads`. Esta cláusula permite al usuario solicitar un número específico de subprocesos para una [construcción paralela](2-directives.md#23-parallel-construct).

- La directiva [threadprivate](2-directives.md#271-threadprivate-directive) se ha ampliado para aceptar variables estáticas de ámbito de bloque.

- Las matrices de longitud variable C99 son tipos completos y se pueden especificar en cualquier lugar en el que se permitan los tipos completos, como en las listas de las cláusulas `private`, `firstprivate`y `lastprivate` (consulte la [sección 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Una variable privada en una región paralela se puede marcar como [privada](2-directives.md#2721-private) de nuevo en una directiva anidada.

- Se ha agregado la cláusula `copyprivate`. Proporciona un mecanismo para usar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor cuando proporcionar este tipo de variable compartida sería difícil (por ejemplo, en una recursividad que requiera una variable diferente en cada nivel). La cláusula [copyprivate](2-directives.md#2728-copyprivate) solo puede aparecer en la Directiva `single`.

- La adición de rutinas de control de tiempo [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) y [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) similares a las rutinas de MPI. Estas funciones son necesarias para realizar los tiempos de reloj de la pared.

- Se ha agregado un apéndice con una lista de [comportamientos definidos por](e-implementation-defined-behaviors-in-openmp-c-cpp.md) la implementaciónC++ de OpenMP C/. En estos casos, se requiere una implementación para definir y documentar su comportamiento.

- Los siguientes cambios sirven para aclarar o corregir características en la especificación de API de OpenMP anterior paraC++C/:

  - Se ha aclarado que el comportamiento de [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) y [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) cuando `omp_in_parallel` devuelve un valor distinto de cero es indefinido.

  - Se ha aclarado el [anidamiento de directivas](2-directives.md#29-directive-nesting) cuando se usa Parallel anidado.

  - Se puede llamar a las funciones de [inicialización de bloqueo](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) y [destrucción de bloqueo](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) en una región paralela.

  - Se han agregado nuevos ejemplos al [apéndice a](a-examples.md).
