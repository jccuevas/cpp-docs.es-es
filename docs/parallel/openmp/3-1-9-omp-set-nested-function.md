---
title: 3.1.9 omp_set_nested (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68e5898b8b57814a152ca2ce9ced84a9df8190cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414544"
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested (Función)

El **omp_set_nested ()** función habilita o deshabilita el paralelismo anidado. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_set_nested(int nested);
```

Si *anidada* se evalúa como 0, anidados paralelismo está deshabilitado, el valor predeterminado y las regiones paralelas anidadas se serializan y ejecutadas por el subproceso actual. Si *anidada* se evalúa como un valor distinto de cero, está habilitado paralelismo anidado y regiones en paralelo que están anidadas pueden implementar subprocesos adicionales para formar equipos anidados.

Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde el **omp_in_parallel ()** función devuelve cero. Si se llama desde una parte del programa donde el **omp_in_parallel ()** función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Esta llamada tiene prioridad sobre la **OMP_NESTED** variable de entorno.

Cuando se habilita el paralelismo anidado, el número de subprocesos usados para ejecutar regiones anidadas en paralelo es definido por la implementación. Como resultado, se permiten implementaciones compatibles con OpenMP para serializar regiones anidadas en paralelo incluso cuando se habilita el paralelismo anidado.

## <a name="cross-references"></a>Referencias cruzadas:

- **OMP_NESTED** vea variable de entorno [sección 4.4](../../parallel/openmp/4-4-omp-nested.md) en la página 49.

- **omp_in_parallel ()** de función, vea [sección 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) en página 38.