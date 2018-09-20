---
title: A.28 uso de la cláusula num_threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 26238da1-902c-49b4-9559-0fbc9eaf7f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fb0111645e1dba42fdd3fa28a885d1ce179ef6f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387924"
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