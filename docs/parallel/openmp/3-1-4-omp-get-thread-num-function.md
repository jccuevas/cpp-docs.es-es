---
title: 3.1.4 omp_get_thread_num (Función)
ms.date: 11/04/2016
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
ms.openlocfilehash: eca8522aeab4702be390d98faaf8920f2d732244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480943"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num (Función)

El `omp_get_thread_num` función devuelve el número de subprocesos dentro de su equipo, del subproceso que ejecuta la función. Los archivos de número de subproceso entre 0 y **omp_get_num_threads()**-1, ambos inclusive. El subproceso principal del equipo es 0.

El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_thread_num(void);
```

Si se llama desde una región de la serie, `omp_get_thread_num` devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.

## <a name="cross-references"></a>Referencias cruzadas:

- `omp_get_num_threads` función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.