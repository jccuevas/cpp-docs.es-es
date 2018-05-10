---
title: 3.1.4 omp_get_thread_num (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad749b91470f7834169fe8ed734f1d627aa228e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num (Función)
El `omp_get_thread_num` función devuelve el número de subprocesos, dentro de su equipo, de que el subproceso que ejecuta la función. Los archivos de número subproceso entre 0 y **omp_get_num_threads()**-1, ambos inclusive. El subproceso principal del equipo es 0.  
  
 El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 Si se llama desde una región de la serie, `omp_get_thread_num` devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   `omp_get_num_threads` función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.