---
title: A.12 Usar la directiva atomic
ms.date: 11/04/2016
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
ms.openlocfilehash: 0f75b182e2cae11f0e72d5ca1e67f887294e8f69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504450"
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