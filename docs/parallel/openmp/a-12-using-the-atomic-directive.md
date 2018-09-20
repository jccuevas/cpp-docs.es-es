---
title: A.12 usar la directiva atomic | Microsoft Docs
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
ms.openlocfilehash: 04daed582cfe87f6e4803b30919af3e07037de7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378753"
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

La ventaja de usar el `atomic` directiva en este ejemplo es que permite que las actualizaciones de dos elementos diferentes de x que se produzcan en paralelo. Si un `critical` directiva ([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18) se usa en su lugar, a continuación, todas las actualizaciones a los elementos de *x* se ejecutaría en serie (aunque no en cualquier garantiza el orden).

Tenga en cuenta que el `atomic` directiva se aplica solo a la instrucción de C o C++ le sigue.  Como resultado, los elementos de *y* no se actualiza de forma atómica en este ejemplo.