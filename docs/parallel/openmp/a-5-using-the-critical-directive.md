---
title: Mediante la directiva crítica de A.5 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1a41e9664faaca24b6708c737a044828eb460bd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686261"
---
# <a name="a5---using-the-critical-directive"></a>A.5 Usar la directiva critical
En el ejemplo siguiente se incluye varios `critical` directivas ([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18). El ejemplo muestra un modelo de puesta en cola en el que se quita de la cola y trabajada en una tarea. Para protegerse de la misma tarea de eliminación de la cola de varios subprocesos, la operación de eliminación de cola debe estar en un `critical` sección. Dado que las dos colas en este ejemplo son independientes, están protegidos por `critical` directivas con nombres diferentes, *xaxis* y *eje y*.  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```