---
title: "OpenMP Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OpenMP Functions
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

proporciona vínculos a las funciones utilizadas en el OpenMP API.  
  
 Implementación de Visual C\+\+ del estándar de OpenMP incluye las siguientes funciones.  
  
|Función|Descripción|  
|-------------|-----------------|  
|[omp\_destroy\_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|desinicializa un bloqueo.|  
|[omp\_destroy\_nest\_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|desinicializa un bloqueo encajable.|  
|[omp\_get\_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Devuelve un valor que indica si el número de subprocesos disponibles en la región paralela subsiguiente se puede ajustar el motor en tiempo de ejecución.|  
|[omp\_get\_max\_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Devuelve un entero al que sea igual o mayor que el número de subprocesos que estará disponible si una región paralela sin [num\_threads](../../../parallel/openmp/reference/num-threads.md) estaba definido en ese momento en el código.|  
|[omp\_get\_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Devuelve un valor que indica si se habilita el paralelismo anidados.|  
|[omp\_get\_num\_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Devuelve el número de procesadores disponibles cuando se llama a la función.|  
|[omp\_get\_num\_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Devuelve el número de subprocesos de la región paralela.|  
|[omp\_get\_thread\_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Devuelve el número de subprocesos del subproceso que se ejecuta dentro del equipo de subproceso.|  
|[omp\_get\_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Devuelve el número de segundos entre los tic\-tac de reloj de procesador.|  
|[omp\_get\_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Devuelve un valor en segundos de tiempo transcurrido de algún punto.|  
|[omp\_in\_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Devuelve cero si se llama dentro de una región paralela.|  
|[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Inicializa un bloqueo simple.|  
|[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Inicializa un bloqueo.|  
|[omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Indica que el número de subprocesos disponibles en la región paralela subsiguiente se puede ajustar el motor en tiempo de ejecución.|  
|[omp\_set\_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Los bloques muestra la ejecución hasta que un bloqueo esté disponible.|  
|[omp\_set\_nest\_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Los bloques muestra la ejecución hasta que un bloqueo esté disponible.|  
|[omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Paralelismo anidado de permisos.|  
|[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Establece el número de subprocesos en regiones paralelas posteriores, a menos que se reemplace con una cláusula de [num\_threads](../../../parallel/openmp/reference/num-threads.md) .|  
|[omp\_test\_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Los intentos de establecer un bloqueo pero no bloquean la ejecución de subprocesos.|  
|[omp\_test\_nest\_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Los intentos de establecer un bloqueo encajable pero no bloquean la ejecución de subprocesos.|  
|[omp\_unset\_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Libere un bloqueo.|  
|[omp\_unset\_nest\_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Libere un bloqueo encajable.|  
  
## Vea también  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)