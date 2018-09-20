---
title: 3.1.2 omp_get_num_threads (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 512c09b0cf71a7fd9c7438b6f9cceb9f16126718
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424990"
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads (Función)

El **omp_get_num_threads ()** función devuelve el número de subprocesos actualmente en el equipo de ejecución de la región paralela desde el que se llama. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_num_threads(void);
```

El **num_threads** cláusula, el **omp_set_num_threads ()** función y el **OMP_NUM_THREADS** variable de entorno controlar el número de subprocesos en un equipo.

Si el número de subprocesos no se ha establecido explícitamente por el usuario, el valor predeterminado es definido por la implementación. Esta función se enlaza a la envolvente más cercana **paralelo** directiva. Si se llama desde una parte de la serie de un programa, o desde una región paralela anidada que se serializa, esta función devuelve 1.

## <a name="cross-references"></a>Referencias cruzadas:

- **OMP_NUM_THREADS** vea variable de entorno [4.2 sección](../../parallel/openmp/4-2-omp-num-threads.md) en página 48.

- **num_threads** cláusula, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.

- **paralelo** construir, consulte [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.