---
title: E. Comportamientos definidos por la implementación de OpenMP C/C++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e866eee9c6d85e93388f9f1d086badf948e2600e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215051"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Comportamientos definidos por la implementación de OpenMP C/C++

En este apéndice se resumen los comportamientos que se describen como "definidos por la implementación" en esta API.  Cada comportamiento es una referencia cruzada a su descripción en la especificación principal.

## <a name="remarks"></a>Observaciones

Se requiere una implementación para definir y documentar su comportamiento en estos casos, pero esta lista puede estar incompleta.

- **Número de subprocesos:** Si se encuentra una región paralela mientras se deshabilita el ajuste dinámico del número de subprocesos y el número de subprocesos solicitados para la región paralela es mayor que el número que el sistema en tiempo de ejecución puede proporcionar, el comportamiento del programa está definido por la implementación (vea la página 9).

   En Visual C++, para una región paralela no anidada, se proporcionarán 64 subprocesos (el máximo).

- **Número de procesadores:** El número de procesadores físicos que hospedan realmente los subprocesos en un momento dado está definido por la implementación (vea la página 10).

   En Visual C++, este número no es constante y lo controla el sistema operativo.

- **Crear equipos de subprocesos:** El número de subprocesos de un equipo que ejecutan una región paralela anidada está definido por la implementación (vea la página 10).

   En Visual C++, este número está determinado por el sistema operativo.

- **programación (tiempo de ejecución):** La decisión sobre la programación se aplaza hasta el tiempo de ejecución. El tipo de programación y el tamaño del fragmento se pueden elegir en tiempo de ejecución si se establece la variable de entorno `OMP_SCHEDULE`. Si no se establece esta variable de entorno, la programación resultante está definida por la implementación (vea la página 13).

   En Visual C++, el tipo de programación es `static` sin tamaño de fragmento.

- **Programación predeterminada:** En ausencia de la cláusula Schedule, la programación predeterminada está definida por la implementación (vea la página 13).

   En Visual C++, el tipo de programación predeterminado es `static` sin tamaño de fragmento.

- **Atómico:** Está definido por la implementación si una implementación reemplaza todas las directivas de `atomic` con directivas de `critical` que tienen el mismo nombre único (vea la página 20).

   En Visual C++, si los datos modificados por [Atomic](reference/openmp-directives.md#atomic) no están en una alineación natural o si son de uno o dos bytes de longitud, todas las operaciones atómicas que cumplan esa propiedad utilizarán una sección crítica. De lo contrario, no se utilizarán secciones críticas.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Si el usuario no ha establecido explícitamente el número de subprocesos, el valor predeterminado es definido por la implementación (vea la página 9).

   En Visual C++, el número predeterminado de subprocesos es igual al número de procesadores.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** El valor predeterminado para el ajuste de subproceso dinámico está definido por la implementación.

   En Visual C++, el valor predeterminado es `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Cuando el paralelismo anidado está habilitado, el número de subprocesos utilizados para ejecutar regiones paralelas anidadas está definido por la implementación.

   En Visual C++, el número de subprocesos viene determinado por el sistema operativo.

- Variable de entorno de [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) : el valor predeterminado de esta variable de entorno está definido por la implementación.

   En Visual C++, el tipo de programación es `static` sin tamaño de fragmento.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable de entorno: Si no se especifica ningún valor para la variable de entorno `OMP_NUM_THREADS` o si el valor especificado no es un entero positivo, o si el valor es mayor que el número máximo de subprocesos que el sistema puede admitir, el número de subprocesos que se van a usar está definido por la implementación.

   En Visual C++, si el valor especificado es cero o menos, el número de subprocesos es igual al número de procesadores.  Si el valor es mayor que 64, el número de subprocesos es 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable de entorno: el valor predeterminado es definido por la implementación.

   En Visual C++, el valor predeterminado es `FALSE`.
