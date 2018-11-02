---
title: A.6 Usar la cláusulas lastprivate
ms.date: 11/04/2016
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
ms.openlocfilehash: 7d5ba1413827590b7fb3afa0847b9aa1da3c41e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579811"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6 Usar la cláusulas lastprivate

A veces, la ejecución correcta depende del valor que la última iteración de un bucle que se asigna a una variable. Estos programas deben enumerar todas las variables como argumentos a un `lastprivate` cláusula ([sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en página 27) para que los valores de las variables son el mismo que cuando se ejecuta el bucle secuencial.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

En el ejemplo anterior, el valor de `i` será igual al final de la región paralela `n-1`, como en el caso secuencial.