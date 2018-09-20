---
title: Directivas for anidadas A.18 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ae2b2e0b-ec94-43f8-928c-6d621b51f0df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4e8a984a111d409e07d55c0c1f6e6adbed91e4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433574"
---
# <a name="a18---nested-for-directives"></a>A.18 Directivas for anidadas

El siguiente ejemplo de `for` anidamiento de directivas ([sección 2.9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33) es compatible con porque el interior y exterior `for` directivas enlazar a diferentes regiones en paralelo:

```
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

Una variación siguiente del ejemplo anterior también es compatible con:

```
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```