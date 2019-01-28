---
title: E. Definido por la implementación de comportamientos en OpenMP C/C ++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087228"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Definido por la implementación de comportamientos en OpenMP C/C ++

En este apéndice se resume los comportamientos que se describen como "definido por la implementación" en esta API.  Cada comportamiento es referencia cruzada en su descripción en la especificación principal.

## <a name="remarks"></a>Comentarios

Una implementación es necesaria para definir y documentar su comportamiento en estos casos, pero esta lista puede estar incompleta.

- **Número de subprocesos:** Si se encuentra una región paralela mientras está deshabilitado el ajuste dinámico del número de subprocesos, y el número de subprocesos solicitado para la región paralela es mayor que el número que puede proporcionar el sistema de tiempo de ejecución, el comportamiento del programa es definido por la implementación (consulte la página 9).

   En Visual C++, para una región paralela no anidados, 64 subprocesos (el máximo) se proporcionará.

- **Número de procesadores:** El número de procesadores físicos hospedando en realidad los subprocesos en un momento dado está definido por la implementación (consulte la página 10).

   En Visual C++, este número no es constante y se controla mediante el sistema operativo.

- **Creación de equipos de subprocesos:** El número de subprocesos en un equipo que ejecute una región paralela anidada está definido por la implementación (consulte la página 10).

   En Visual C++, este número se determina por el sistema operativo.

- **Schedule (Runtime):** La decisión sobre la programación se pospone hasta el tiempo de ejecución. Se puede elegir el tamaño de tipo y el fragmento de la programación en tiempo de ejecución estableciendo la `OMP_SCHEDULE` variable de entorno. Si no se establece esta variable de entorno, el plan resultante está definido por la implementación (consulte la página 13).

   En Visual C++, es el tipo de programación `static` con ningún tamaño de fragmento.

- **Valor predeterminado de programación:** En ausencia de la cláusula de programación, la programación predeterminada es definido por la implementación (consulte la página 13).

   En Visual C++, es el tipo de programación predeterminado `static` con ningún tamaño de fragmento.

- **ATÓMICA:** Está definido por la implementación si una implementación reemplaza toda `atomic` directivas con `critical` directivas que tienen el mismo nombre único (consulte la página 20).

   En Visual C++, si los datos modificados por [atómica](reference/openmp-directives.md#atomic) no se encuentra en una alineación natural o si es larga uno o dos bytes, todas las operaciones atómicas que satisfacen esa propiedad va a utilizar una sección crítica. En caso contrario, secciones críticas no se usará.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Si el número de subprocesos no se ha establecido explícitamente por el usuario, el valor predeterminado es definido por la implementación (consulte la página 9).

   En Visual C++, el número predeterminado de subprocesos es igual al número de procesadores.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** El valor predeterminado para el ajuste dinámico del subproceso está definido por la implementación.

   En Visual C++, el valor predeterminado es `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Cuando se habilita el paralelismo anidado, el número de subprocesos usados para ejecutar regiones anidadas en paralelo es definido por la implementación.

   En Visual C++, el número de subprocesos viene determinada por el sistema operativo.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) variable de entorno: El valor predeterminado de esta variable de entorno es definido por la implementación.

   En Visual C++, es el tipo de programación `static` con ningún tamaño de fragmento.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable de entorno: Si se especifica ningún valor para el `OMP_NUM_THREADS` variable de entorno, o si el valor especificado no es un entero positivo, o si el valor es mayor que el número máximo de subprocesos puede admitir el sistema, el número de subprocesos que se utilizarán es definido por la implementación.

   En Visual C++, si especifica el valor es cero o menos, el número de subprocesos es igual al número de procesadores.  Si el valor es mayor que 64, el número de subprocesos es 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable de entorno: El valor predeterminado es definido por la implementación.

   En Visual C++, el valor predeterminado es `FALSE`.