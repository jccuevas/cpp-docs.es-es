---
title: 4.2 OMP_NUM_THREADS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c2b766d0e3be9b4f1d272a6e3fa205cfcb87039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS
El **OMP_NUM_THREADS** variable de entorno establece el número predeterminado de subprocesos que se utilizarán durante la ejecución, a menos que dicho número se cambia explícitamente mediante una llamada a la **omp_set_num_threads ()** rutina de biblioteca o por explícito **num_threads** cláusula en una **paralelo** directiva.  
  
 El valor de la **OMP_NUM_THREADS** variable de entorno debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para un conjunto completo de reglas sobre la interacción entre el **OMP_NUM_THREADS** entorno ajuste variable y dinámico de subprocesos, vea la sección 2.3 en página 8.  
  
 Si se especifica ningún valor para el **OMP_NUM_THREADS** variable de entorno, o si el valor especificado no es un entero positivo, o si el valor es mayor que el número máximo de subprocesos que el sistema puede admitir, el número de subprocesos que se utilizarán está definido por la implementación.  
  
 Ejemplo:  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **num_threads** cláusula, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8.  
  
-   **omp_set_num_threads ()** función, vea [punto 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.  
  
-   **omp_set_dynamic ()** función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.