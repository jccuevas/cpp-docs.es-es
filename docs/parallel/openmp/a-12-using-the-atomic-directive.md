---
title: A.12 mediante la directiva atómica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719d7a9843a0759b5a5bd558e07a2004f9ef1543
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a12---using-the-atomic-directive"></a>A.12 Usar la directiva atomic
En el ejemplo siguiente, se evita las condiciones de carrera (actualizaciones simultáneas de un elemento de *x* varios subprocesos) mediante el uso de la `atomic` directiva ([sección 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) en la página 19):  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 La ventaja de utilizar el `atomic` (directiva) en este ejemplo es que permite a las actualizaciones de dos elementos distintos de x que se produzcan en paralelo. Si un `critical` directiva ([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18) se usa en su lugar, todas las actualizaciones a los elementos de *x* se ejecutaría en serie (aunque no en cualquier garantiza el orden).  
  
 Tenga en cuenta que el `atomic` directiva se aplica solo a la instrucción de C o C++ sigue inmediatamente.  Como resultado, los elementos de *y* no se actualiza de forma atómica en este ejemplo.