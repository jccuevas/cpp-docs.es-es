---
title: 3.1.8 omp_get_dynamic (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c30f49eaf91353d6a7cd9bd26e0e10e95cb6acd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426788"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic (Función)

El **omp_get_dynamic ()** función devuelve un valor distinto de cero si realizar un ajuste dinámico de subprocesos está habilitado y lo contrario, devuelve 0. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_dynamic(void);
```

Si la implementación no implementa un ajuste dinámico del número de subprocesos, esta función siempre devuelve 0.

## <a name="cross-references"></a>Referencias cruzadas:

- Para obtener una descripción de ajuste dinámico del subproceso, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.