---
title: Uso A.28 de num_threads cláusula | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 26238da1-902c-49b4-9559-0fbc9eaf7f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12289192d056acac684f28712ccf2aa1423b6c3e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a28---use-of-numthreads-clause"></a>A.28 Uso de la cláusula num_threads
En el ejemplo siguiente se muestra la `num_threads` cláusula ([sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8). La región paralela se ejecuta con un máximo de 10 subprocesos.  
  
```  
#include <omp.h>  
main()  
{  
    omp_set_dynamic(1);  
    ...  
    #pragma omp parallel num_threads(10)  
    {  
        ... parallel region ...  
    }  
}  
```