---
title: A.3 usar regiones paralelas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82bc1655584af300cb2d36a62250595839d74551
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413086"
---
# <a name="a3---using-parallel-regions"></a>A.3 Usar regiones paralelas

El `parallel` directiva ([sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8) se pueden usar en programas paralelos más generales. En el ejemplo siguiente, cada subproceso de la región paralela decide qué parte de la matriz global `x` que trabajar, en función del número de subprocesos:

```
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```