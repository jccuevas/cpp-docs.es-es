---
title: 3.1.3 omp_get_max_threads (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2afa797cc74a50041f2ea24f76fa07ffe109072b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads (Función)
El **omp_get_max_threads ()** función devuelve un entero que se garantiza que sea al menos tan grande como el número de subprocesos que se utilizarían para formar un equipo si una región paralela sin un **num_threads** cláusula tuviera que se encuentra en ese momento en el código. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 El siguiente expresa un límite inferior en el valor de **omp_get_max_threads ()**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 Tenga en cuenta que si usa una región paralela posterior el **num_threads** cláusula para solicitar un número específico de subprocesos, la garantía en el límite inferior del resultado de **omp_get_max_threads ()** no contiene largo.  
  
 El **omp_get_max_threads ()** valor devuelto de la función puede utilizarse para asignar dinámicamente suficiente espacio de almacenamiento para todos los subprocesos en el equipo de forma en la región paralela posterior.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **omp_get_num_threads ()** función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.  
  
-   **omp_set_num_threads ()** función, vea [punto 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.  
  
-   **omp_set_dynamic ()** función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.  
  
-   **num_threads** cláusula, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8.