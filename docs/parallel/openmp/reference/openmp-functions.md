---
title: Funciones de OpenMP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39fe44ff053a2e49a1067d0af071353e0a50ece
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-functions"></a>Funciones de OpenMP
Proporciona vínculos a las funciones que se utilizan en la API de OpenMP.  
  
 La implementación de Visual C++ de la OpenMP estándar incluye las siguientes funciones.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|Anula la inicialización de un bloqueo.|  
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|Anula la inicialización de un bloqueo anidable.|  
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Devuelve un valor que indica si el número de subprocesos disponibles en la región paralela posterior puede ser ajustado por el tiempo de ejecución.|  
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Devuelve un entero que es igual o mayor que el número de subprocesos que estaría disponible si una región paralela sin [num_threads](../../../parallel/openmp/reference/num-threads.md) se define en ese momento en el código.|  
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Devuelve un valor que indica si está habilitado el paralelismo anidado.|  
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Devuelve el número de procesadores que están disponibles cuando se llama a la función.|  
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Devuelve el número de subprocesos en la región paralela.|  
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Devuelve el número de subprocesos de la ejecución de subprocesos dentro de su equipo de subproceso.|  
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Devuelve el número de segundos entre ciclos de reloj de procesador.|  
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Devuelve que un valor en segundos del tiempo transcurrido en algún momento.|  
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Devuelve un valor distinto de cero si se llama desde dentro de una región paralela.|  
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Inicializa un bloqueo simple.|  
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Inicializa un bloqueo.|  
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Indica que el número de subprocesos disponibles en la región paralela posterior puede ser ajustado por el tiempo de ejecución.|  
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Bloques de ejecución del subproceso hasta que haya un bloqueo disponible.|  
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Bloques de ejecución del subproceso hasta que haya un bloqueo disponible.|  
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Habilita el paralelismo anidado.|  
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Establece el número de subprocesos en regiones posteriores en paralelo, a menos que se reemplaza por un [num_threads](../../../parallel/openmp/reference/num-threads.md) cláusula.|  
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Intenta establecer un bloqueo, pero no impide la ejecución de subprocesos.|  
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Intenta establecer un bloqueo anidable pero no impide la ejecución de subprocesos.|  
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Libera un bloqueo.|  
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Libera un bloqueo anidable.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca](../../../parallel/openmp/reference/openmp-library-reference.md)