---
title: A.10 Especificar un orden secuencial
ms.date: 11/04/2016
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
ms.openlocfilehash: 4e3a146e1bca988f46cf7a7ee504644f96dab67e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575258"
---
# <a name="a10---specifying-sequential-ordering"></a>A.10 Especificar un orden secuencial

Ordenada secciones ([sección 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) en la página 22) son útiles para ordenar la salida de trabajo que se realiza en paralelo de secuencialmente. El siguiente programa imprime los índices en orden secuencial:

```
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```