---
title: A.28 Uso de la cláusula num_threads
ms.date: 11/04/2016
ms.assetid: 26238da1-902c-49b4-9559-0fbc9eaf7f36
ms.openlocfilehash: 99dd327d0a97f561107ffaa6a6ed1435e3772a41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492304"
---
# <a name="a28---use-of-numthreads-clause"></a>A.28 Uso de la cláusula num_threads

En el ejemplo siguiente se muestra el `num_threads` cláusula ([sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8). La región paralela se ejecuta con un máximo de 10 subprocesos.

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