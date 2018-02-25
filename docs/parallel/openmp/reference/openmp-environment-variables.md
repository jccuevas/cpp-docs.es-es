---
title: Las Variables de entorno de OpenMP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7e0089399cd1a6d91a1324d8c986ea22c1fae63
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="openmp-environment-variables"></a>Variables de entorno de OpenMP
Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.  
  
 La implementación de Visual C++ de la OpenMP estándar incluye las siguientes variables de entorno. Estas variables de entorno se leen al inicio del programa y se pasan por alto las modificaciones realizadas en sus valores en tiempo de ejecución (por ejemplo, si se usa [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).  
  
|Variable de entorno|Descripción|  
|--------------------------|-----------------|  
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.|  
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Especifica si está habilitado paralelismo anidado, a menos que paralelismo anidado está habilitado o deshabilitado con `omp_set_nested`.|  
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num_threads](../../../parallel/openmp/reference/num-threads.md).|  
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Modifica el comportamiento de la [programación](../../../parallel/openmp/reference/schedule.md) cláusula cuando `schedule(runtime)` se especifica en un `for` o `parallel for` directiva.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca](../../../parallel/openmp/reference/openmp-library-reference.md)