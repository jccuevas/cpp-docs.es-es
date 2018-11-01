---
title: 3.1.3 omp_get_max_threads (Función)
ms.date: 11/04/2016
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
ms.openlocfilehash: 3f954b5ad75b4bdb4a74323f2ab4e819850269ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546597"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads (Función)

El **omp_get_max_threads ()** función devuelve un entero que se garantiza que sea al menos tan grande como el número de subprocesos que se usaría para formar un equipo si una región paralela sin un **num_threads** cláusula tuviera que se encuentra en ese momento en el código. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_max_threads(void);
```

La siguiente expresa un límite inferior del valor de **omp_get_max_threads ()**:

```

threads-used-for-next-team
<= omp_get_max_threads

```

Tenga en cuenta que si usa una región paralela posteriores el **num_threads** cláusula para solicitar un número específico de subprocesos, la garantía en el límite inferior del resultado de **omp_get_max_threads ()** no contiene mucho.

El **omp_get_max_threads ()** valor devuelto de la función puede utilizarse para asignar dinámicamente suficiente espacio de almacenamiento para todos los subprocesos en el equipo tiene el formato en la región paralela posteriores.

## <a name="cross-references"></a>Referencias cruzadas:

- **omp_get_num_threads ()** de función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.

- **omp_set_num_threads ()** de función, vea [sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.

- **omp_set_dynamic ()** de función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.

- **num_threads** cláusula, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.