---
title: 4.3 OMP_DYNAMIC
ms.date: 11/04/2016
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
ms.openlocfilehash: 0ea6784159a11fc194d0c1cd16d2316a80b9cd37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488574"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

El **OMP_DYNAMIC** variable de entorno habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de las regiones en paralelo, a menos que realizar un ajuste dinámico explícitamente está habilitado o deshabilitado mediante una llamada a la **omp_set_dynamic ()** rutina de biblioteca. Su valor debe ser **TRUE** o **FALSE**.

Si establece en **TRUE**, se puede ajustar el número de subprocesos que se utilizan para la ejecución de regiones en paralelo por el entorno de tiempo de ejecución para usar mejor los recursos del sistema.  Si establece en **FALSE**, realizar un ajuste dinámico está deshabilitado. La condición predeterminada es definido por la implementación.

Ejemplo:

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>Referencias cruzadas:

- Para obtener más información sobre las regiones en paralelo, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.

- **omp_set_dynamic ()** de función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.