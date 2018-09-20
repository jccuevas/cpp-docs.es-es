---
title: A.4 usar la cláusula nowait | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da4b69ed8ccf59fb90d17da2b85d7693d661785b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444507"
---
# <a name="a4---using-the-nowait-clause"></a>A.4 Usar la cláusula nowait

Si hay varios bucles independientes dentro de una región paralela, puede usar el `nowait` cláusula ([sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11) para evitar la barrera implícita al final de la `for` directiva, como se indica a continuación:

```
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```