---
title: 4.3 OMP_DYNAMIC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c15fa9d8c9d86b736bfc577a3b17e9809ec9baaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439203"
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