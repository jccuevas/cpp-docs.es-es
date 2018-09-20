---
title: A.5 usar la directiva critical | Microsoft Docs
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
ms.openlocfilehash: 99f9ab513ae1df5a7e1e62cfefcefe404637c063
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444572"
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