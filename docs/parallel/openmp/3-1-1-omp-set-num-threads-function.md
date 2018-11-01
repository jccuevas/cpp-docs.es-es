---
title: 3.1.1 omp_set_num_threads (Función)
ms.date: 11/04/2016
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
ms.openlocfilehash: 20b6b6ced2b4031696f1d019604842ae9b91bda2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663286"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads (Función)

El `omp_set_num_threads` función establece el número predeterminado de subprocesos que se usará para regiones paralelas posteriores que no especifican un `num_threads` cláusula. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

El valor del parámetro *num_threads* debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para un conjunto completo de reglas sobre la interacción entre el `omp_set_num_threads` función y realizar un ajuste dinámico de subprocesos, consulte la sección 2.3 en la página 8.

Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde el `omp_in_parallel` función devuelve cero. Si se llama desde una parte del programa donde el `omp_in_parallel` función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene prioridad sobre la `OMP_NUM_THREADS` variable de entorno. El valor predeterminado para el número de subprocesos, lo que se pueden establecer mediante una llamada a `omp_set_num_threads` o estableciendo la `OMP_NUM_THREADS` variable de entorno, se pueden reemplazar explícitamente en una sola **paralelo** la directiva mediante la especificación de la `num_threads` cláusula.

## <a name="cross-references"></a>Referencias cruzadas:

- `omp_set_dynamic` función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.

- `omp_get_dynamic` función, vea [sección 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) en la página 40.

- `OMP_NUM_THREADS` vea variable de entorno [4.2 sección](../../parallel/openmp/4-2-omp-num-threads.md) en página 48, sección 2.3 en página 8.

- `num_threads` cláusula, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8