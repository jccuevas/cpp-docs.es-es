---
title: A.5 Usar la directiva critical
ms.date: 11/04/2016
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
ms.openlocfilehash: 82497d63acc057fbbcf26f585e42fc8611c08ec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545112"
---
# <a name="a5---using-the-critical-directive"></a>A.5 Usar la directiva critical

En el ejemplo siguiente se incluyen varios `critical` directivas ([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18). El ejemplo muestra un modelo de puesta en cola en el que se quita de la cola y trabajó en una tarea. Para protegerse contra la misma tarea quitar de la cola de varios subprocesos, la operación de eliminación de cola debe estar en un `critical` sección. Dado que las dos colas en este ejemplo son independientes, están protegidos por `critical` directivas con nombres diferentes, *valor* y *eje y*.

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