---
title: "OpenMP Environment Variables | Microsoft Docs"
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
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# OpenMP Environment Variables
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

proporciona vínculos a las variables de entorno utilizadas en el OpenMP API.  
  
 Implementación de Visual C\+\+ del estándar de OpenMP incluye las siguientes variables de entorno.  Estas variables de entorno se leen en el inicio del programa y modificaciones a sus valores se omiten en tiempo de ejecución \(por ejemplo, mediante [\_putenv, \_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)\).  
  
|Variable de entorno|Descripción|  
|-------------------------|-----------------|  
|[OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Especifica si el runtime de OpenMP puede ajustar el número de subprocesos en una región paralela.|  
|[OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Especifica si el paralelismo anidados está habilitado, a menos que el paralelismo anidados está habilitado o deshabilitado con `omp_set_nested`.|  
|[OMP\_NUM\_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Establece el número máximo de subprocesos de la región paralela, a menos que se reemplace con [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num\_threads](../../../parallel/openmp/reference/num-threads.md).|  
|[OMP\_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|modifica el comportamiento de la cláusula de [schedule](../../../parallel/openmp/reference/schedule.md) cuando `schedule(runtime)` se especifica en una directiva de `for` o de `parallel for` .|  
  
## Vea también  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)