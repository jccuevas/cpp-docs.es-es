---
title: E. Definido por la implementación de comportamientos en OpenMP C/C ++
ms.date: 11/04/2016
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 704062f36102a06e6e7b8cf015f6330f925a6bba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619354"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Definido por la implementación de comportamientos en OpenMP C/C ++

En este apéndice se resume los comportamientos que se describen como "definido por la implementación" en esta API.  Cada comportamiento es referencia cruzada en su descripción en la especificación principal.

## <a name="remarks"></a>Comentarios

Una implementación es necesaria para definir y documentar su comportamiento en estos casos, pero esta lista puede estar incompleta.

- **Número de subprocesos:** si se encontró una región paralela al realizar un ajuste dinámico del número de subprocesos está deshabilitado y el número de subprocesos solicitado para la región paralela supera el número que puede proporcionar el sistema de tiempo de ejecución, el comportamiento de el programa está definido por la implementación (consulte la página 9).

   En Visual C++, para una región paralela no anidados, 64 subprocesos (el máximo) se proporcionará.

- **Número de procesadores:** el número de procesadores físicos hospedando en realidad los subprocesos en un momento dado está definido por la implementación (consulte la página 10).

   En Visual C++, este número no es constante y se controla mediante el sistema operativo.

- **Creación de equipos de subprocesos:** el número de subprocesos en un equipo que ejecute una región paralela anidada es definido por la implementación. () Consulte la página 10).

   En Visual C++, esto viene determinado por el sistema operativo.

- **Schedule (Runtime):** la decisión sobre la programación se retrasa hasta el tiempo de ejecución. Se puede elegir el tamaño de tipo y el fragmento de la programación en tiempo de ejecución estableciendo la `OMP_SCHEDULE` variable de entorno. Si no se establece esta variable de entorno, el plan resultante está definido por la implementación (consulte la página 13).

   En Visual C++, es el tipo de programación `static` con ningún tamaño de fragmento.

- **Programación predeterminada:** en ausencia de la cláusula de programación, la programación predeterminada se define en la implementación (consulte la página 13).

   En Visual C++, es el tipo de programación predeterminado `static` con ningún tamaño de fragmento.

- **ATÓMICA:** es definido por la implementación si una implementación reemplaza toda `atomic` directivas con **críticos** directivas que tienen el mismo nombre único (consulte la página 20).

   En Visual C++, si los datos modificados por [atómica](../../parallel/openmp/reference/atomic.md) no está en una alineación natural o si es 1 o 2 bytes larga todas las operaciones atómicas que satisfacen esa propiedad va a utilizar una sección crítica. En caso contrario, secciones críticas no se usará.

- **omp_get_num_threads ():** si el número de subprocesos no se ha establecido explícitamente por el usuario, el valor predeterminado es definido por la implementación (consulte la página 9, y [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37).

   En Visual C++, el número predeterminado de subprocesos es igual al número de procesadores.

- **omp_set_dynamic ():** el valor predeterminado para el ajuste dinámico del subproceso está definido por la implementación (consulte [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39).

   En Visual C++, el valor predeterminado es `FALSE`.

- **omp_set_nested ():** cuando se habilita el paralelismo anidado, el número de subprocesos usados para ejecutar regiones anidadas en paralelo es definido por la implementación (consulte [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40).

   En Visual C++, el número de subprocesos viene determinada por el sistema operativo.

- `OMP_SCHEDULE` variable de entorno: el valor predeterminado de esta variable de entorno es definido por la implementación (consulte [sección 4.1](../../parallel/openmp/4-1-omp-schedule.md) en página 48).

   En Visual C++, es el tipo de programación `static` con ningún tamaño de fragmento.

- `OMP_NUM_THREADS` variable de entorno: si se especifica ningún valor para el `OMP_NUM_THREADS` variable de entorno, o si el valor especificado no es un entero positivo, o si el valor es mayor que el número máximo de subprocesos puede admitir el sistema, es el número de subprocesos para usar definido por la implementación (consulte [4.2 sección](../../parallel/openmp/4-2-omp-num-threads.md) en página 48).

   En Visual C++, si especifica el valor es cero o menos, el número de subprocesos es igual al número de procesadores.  Si el valor es mayor que 64, el número de subprocesos es 64.

- `OMP_DYNAMIC` variable de entorno: el valor predeterminado es definido por la implementación (consulte [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49).

   En Visual C++, el valor predeterminado es `FALSE`.