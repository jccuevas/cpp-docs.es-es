---
title: A.15 Determinar el número de subprocesos utilizados
ms.date: 11/04/2016
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
ms.openlocfilehash: bd5e897eeab35ec73c061d2ae02a4b85772e1255
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525854"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15 Determinar el número de subprocesos utilizados

Considere el siguiente ejemplo incorrecto (para [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37):

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

El `omp_get_num_threads()` llamada devuelve 1 en la sección de serie del código, por lo que *np* siempre será igual a 1 en el ejemplo anterior. Para determinar el número de subprocesos que se implementarán para la región paralela, debe ser la llamada dentro de la región paralela.

El ejemplo siguiente muestra cómo volver a escribir este programa sin necesidad de incluir una consulta para el número de subprocesos:

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```