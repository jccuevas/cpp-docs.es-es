---
title: Contenido | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b7858099-7d7f-4cd9-9fa0-fba4832f2dd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0ed7dd48d496042cb48a8c8054226ec8892ffbc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432768"
---
# <a name="contents"></a>Contenido

[1. Introducción](../../parallel/openmp/1-introduction.md)

[1.1 Ámbito](../../parallel/openmp/1-1-scope.md)

[1.2 Definición de términos](../../parallel/openmp/1-2-definition-of-terms.md)

[1.3 Modelo de ejecución](../../parallel/openmp/1-3-execution-model.md)

[1.4 Conformidad](../../parallel/openmp/1-4-compliance.md)

[1.5 Referencias de normativa](../../parallel/openmp/1-5-normative-references.md)

[1.6 Organización](../../parallel/openmp/1-6-organization.md)

[2. Directivas](../../parallel/openmp/2-directives.md)

[2.1 Formato de directivas](../../parallel/openmp/2-1-directive-format.md)

[2.2 Compilación condicional](../../parallel/openmp/2-2-conditional-compilation.md)

[2.3 parallel (construcción)](../../parallel/openmp/2-3-parallel-construct.md)

[2.4 Construcciones de uso compartido](../../parallel/openmp/2-4-work-sharing-constructs.md)

[2.4.1 for (construcción)](../../parallel/openmp/2-4-1-for-construct.md)

[2.4.2 sections (construcción)](../../parallel/openmp/2-4-2-sections-construct.md)

[2.4.3 single (construcción)](../../parallel/openmp/2-4-3-single-construct.md)

[2.5 Construcciones de uso compartido paralelas combinadas](../../parallel/openmp/2-5-combined-parallel-work-sharing-constructs.md)

[2.5.1 parallel for (construcción)](../../parallel/openmp/2-5-1-parallel-for-construct.md)

[2.5.2 parallel sections (construcción)](../../parallel/openmp/2-5-2-parallel-sections-construct.md)

[2.6 Directivas maestras y de sincronización](../../parallel/openmp/2-6-master-and-synchronization-directives.md)

[2.6.1 master (construcción)](../../parallel/openmp/2-6-1-master-construct.md)

[2.6.2 critical (construcción)](../../parallel/openmp/2-6-2-critical-construct.md)

[2.6.3 barrier (directiva)](../../parallel/openmp/2-6-3-barrier-directive.md)

[2.6.4 atomic (construcción)](../../parallel/openmp/2-6-4-atomic-construct.md)

[2.6.5 flush (directiva)](../../parallel/openmp/2-6-5-flush-directive.md)

[2.6.6 ordered (construcción)](../../parallel/openmp/2-6-6-ordered-construct.md)

[2.7 Entorno de datos](../../parallel/openmp/2-7-data-environment.md)

[2.7.1 threadprivate (directiva)](../../parallel/openmp/2-7-1-threadprivate-directive.md)

[2.7.2 Cláusulas de atributos de uso compartido de datos](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)

[2.7.2.1 private](../../parallel/openmp/2-7-2-1-private.md)

[2.7.2.2 firstprivate](../../parallel/openmp/2-7-2-2-firstprivate.md)

[2.7.2.3 lastprivate](../../parallel/openmp/2-7-2-3-lastprivate.md)

[2.7.2.4 shared](../../parallel/openmp/2-7-2-4-shared.md)

[2.7.2.5 default](../../parallel/openmp/2-7-2-5-default.md)

[2.7.2.6 reduction](../../parallel/openmp/2-7-2-6-reduction.md)

[2.7.2.7 copyin](../../parallel/openmp/2-7-2-7-copyin.md)

[2.7.2.8 copyprivate](../../parallel/openmp/2-7-2-8-copyprivate.md)

[2.8 Enlace de directivas](../../parallel/openmp/2-8-directive-binding.md)

[2.9 Anidamiento de directivas](../../parallel/openmp/2-9-directive-nesting.md)

[3. Funciones de biblioteca en tiempo de ejecución](../../parallel/openmp/3-run-time-library-functions.md)

[3.1 Funciones de entorno de ejecución](../../parallel/openmp/3-1-execution-environment-functions.md)

[3.1.1 omp_set_num_threads (función)](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)

[3.1.2 omp_get_num_threads (función)](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)

[3.1.3 omp_get_max_threads (función)](../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)

[3.1.4 omp_get_thread_num (función)](../../parallel/openmp/3-1-4-omp-get-thread-num-function.md)

[3.1.5 omp_get_num_procs (función)](../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)

[3.1.6 omp_in_parallel (función)](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)

[3.1.7 omp_set_dynamic (función)](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)

[3.1.8 omp_get_dynamic (función)](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md)

[3.1.9 omp_set_nested (función)](../../parallel/openmp/3-1-9-omp-set-nested-function.md)

[3.1.10 omp_get_nested (función)](../../parallel/openmp/3-1-10-omp-get-nested-function.md)

[3.2 Funciones de bloqueo](../../parallel/openmp/3-2-lock-functions.md)

[3.2.1 omp_init_lock y omp_init_nest_lock (funciones)](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)

[3.2.2 omp_destroy_lock y omp_destroy_nest_lock (funciones)](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)

[3.2.3 omp_set_lock y omp_set_nest_lock (funciones)](../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)

[3.2.4 omp_unset_lock y omp_unset_nest_lock (funciones)](../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)

[3.2.5 omp_test_lock y omp_test_nest_lock (funciones)](../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)

[3.3 Rutinas temporales](../../parallel/openmp/3-3-timing-routines.md)

[3.3.1 omp_get_wtime (función)](../../parallel/openmp/3-3-1-omp-get-wtime-function.md)

[3.3.2 omp_get_wtick (función)](../../parallel/openmp/3-3-2-omp-get-wtick-function.md)

[4. Variables de entorno](../../parallel/openmp/4-environment-variables.md)

[4.1 OMP_SCHEDULE](../../parallel/openmp/4-1-omp-schedule.md)

[4.2 OMP_NUM_THREADS](../../parallel/openmp/4-2-omp-num-threads.md)

[4.3 OMP_DYNAMIC](../../parallel/openmp/4-3-omp-dynamic.md)

[4.4 OMP_NESTED](../../parallel/openmp/4-4-omp-nested.md)

[A. Ejemplos](../../parallel/openmp/a-examples.md)

[A.1 ejecutar un bucle sencillo en paralelo](../../parallel/openmp/a-1-executing-a-simple-loop-in-parallel.md)

[A.2 especificar una compilación condicional](../../parallel/openmp/a-2-specifying-conditional-compilation.md)

[A.3 usar regiones paralelas](../../parallel/openmp/a-3-using-parallel-regions.md)

[A.4 usar la cláusula nowait](../../parallel/openmp/a-4-using-the-nowait-clause.md)

[A.5 usar la directiva critical](../../parallel/openmp/a-5-using-the-critical-directive.md)

[A.6 usar la cláusula lastprivate](../../parallel/openmp/a-6-using-the-lastprivate-clause.md)

[A.7 usar la cláusula reduction](../../parallel/openmp/a-7-using-the-reduction-clause.md)

[A.8 especificar secciones paralelas](../../parallel/openmp/a-8-specifying-parallel-sections.md)

[A.9 usar directivas single](../../parallel/openmp/a-9-using-single-directives.md)

[A.10 especificar un orden secuencial](../../parallel/openmp/a-10-specifying-sequential-ordering.md)

[A.11 especificar un número fijo de subprocesos](../../parallel/openmp/a-11-specifying-a-fixed-number-of-threads.md)

[A.12 usar la directiva atomic](../../parallel/openmp/a-12-using-the-atomic-directive.md)

[A.13 usar la directiva flush con una lista](../../parallel/openmp/a-13-using-the-flush-directive-with-a-list.md)

[A.14 usar la directiva flush sin una lista](../../parallel/openmp/a-14-using-the-flush-directive-without-a-list.md)

[A.15 determinar el número de subprocesos usados](../../parallel/openmp/a-15-determining-the-number-of-threads-used.md)

[A.16 usar bloqueos](../../parallel/openmp/a-16-using-locks.md)

[A.17 usar bloqueos Anidables](../../parallel/openmp/a-17-using-nestable-locks.md)

[A.18 directivas for anidadas](../../parallel/openmp/a-18-nested-for-directives.md)

[A.19 ejemplos donde se muestra un anidamiento incorrecto de directivas de uso compartido](../../parallel/openmp/a-19-examples-showing-incorrect-nesting-of-work-sharing-directives.md)

[A.20 enlace de directivas barrier](../../parallel/openmp/a-20-binding-of-barrier-directives.md)

[A.21 Variables de ámbito con la cláusula private](../../parallel/openmp/a-21-scoping-variables-with-the-private-clause.md)

[A.22 usar la cláusula default (None)](../../parallel/openmp/a-22-using-the-default-none-clause.md)

[A.23 ejemplos de la directiva ordered](../../parallel/openmp/a-23-examples-of-the-ordered-directive.md)

[A.24 ejemplo de la cláusula private](../../parallel/openmp/a-24-example-of-the-private-clause.md)

[A.25 ejemplos de la cláusula de atributos de datos copyprivate](../../parallel/openmp/a-25-examples-of-the-copyprivate-data-attribute-clause.md)

[A.26 usar la directiva threadprivate](../../parallel/openmp/a-26-using-the-threadprivate-directive.md)

[A.27 uso de matrices de longitud Variable C99](../../parallel/openmp/a-27-use-of-c99-variable-length-arrays.md)

[A.28 uso de la cláusula num_threads](../../parallel/openmp/a-28-use-of-num-threads-clause.md)

[A.29 uso de uso compartido construcciones en una construcción critical](../../parallel/openmp/a-29-use-of-work-sharing-constructs-inside-a-critical-construct.md)

[A.30 uso de la Reprivatización](../../parallel/openmp/a-30-use-of-reprivatization.md)

[A.31 funciones de bloqueo de subprocesos](../../parallel/openmp/a-31-thread-safe-lock-functions.md)

[B. Códigos auxiliares para funciones de biblioteca en tiempo de ejecución](../../parallel/openmp/b-stubs-for-run-time-library-functions.md)

[C. Gramática de OpenMP C y C++](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)

[C.1 Notación](../../parallel/openmp/c-1-notation.md)

[C.2 Reglas](../../parallel/openmp/c-2-rules.md)

[D. Usar la cláusula schedule](../../parallel/openmp/d-using-the-schedule-clause.md)

[E. Comportamientos definidos por la implementación de OpenMP C/C++](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)

[F. Nuevas características y aclaraciones de la versión 2.0](../../parallel/openmp/f-new-features-and-clarifications-in-version-2-0.md)

## <a name="see-also"></a>Vea también

[Interfaz de programación de aplicaciones de C++ y C](../../parallel/openmp/openmp-c-and-cpp-application-program-interface.md)