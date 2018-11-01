---
title: A.27 Uso de matrices de longitud variable C99
ms.date: 11/04/2016
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
ms.openlocfilehash: 7b2ee74dcd5adedd02e7a9b311c5d3f67203d892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655304"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27 Uso de matrices de longitud variable C99

En el ejemplo siguiente se muestra cómo usar matrices de longitud Variable C99 (VLA) en un `firstprivate` directiva ([sección 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) en página 26).

> [!NOTE]
>  Matrices de longitud variable no se admiten actualmente en Visual C++.

```
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```