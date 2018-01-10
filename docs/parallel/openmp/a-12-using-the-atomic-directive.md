---
title: "A.12 mediante la directiva atómica | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9aa619d9bbe635a41d15a39d6c05780a4416520e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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