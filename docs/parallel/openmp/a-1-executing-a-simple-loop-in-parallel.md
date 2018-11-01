---
title: A.1 Ejecutar un bucle sencillo en paralelo
ms.date: 11/04/2016
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
ms.openlocfilehash: 5bd9a9c8b1d226c67f7e9031a547e551fae3407b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558943"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1 Ejecutar un bucle sencillo en paralelo

En el ejemplo siguiente se muestra cómo paralelizar un bucle simple con el `parallel for` directiva ([sección 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) en la página 16). La variable de iteración del bucle es privada de forma predeterminada, por lo que no es necesario especificarla explícitamente en una cláusula privada.

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```