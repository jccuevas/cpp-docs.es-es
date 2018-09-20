---
title: 4.2 OMP_NUM_THREADS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9996a09661d962eb5e936fdb484c9dd534e46904
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445196"
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

El **OMP_NUM_THREADS** variable de entorno establece el número predeterminado de subprocesos que se utilizarán durante la ejecución, a menos que ese número se cambia explícitamente mediante una llamada a la **omp_set_num_threads ()** rutina de biblioteca o por explícita **num_threads** cláusula en una **paralelo** directiva.

El valor de la **OMP_NUM_THREADS** variable de entorno debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para un conjunto completo de reglas sobre la interacción entre el **OMP_NUM_THREADS** entorno ajuste dinámico y variable de subprocesos, consulte la sección 2.3 en la página 8.

Si se especifica ningún valor para el **OMP_NUM_THREADS** variable de entorno, o si el valor especificado no es un entero positivo, o si el valor es mayor que el número máximo de subprocesos del sistema puede admitir, el número de subprocesos para usar está definido por la implementación.

Ejemplo:

```
setenv OMP_NUM_THREADS 16
```

## <a name="cross-references"></a>Referencias cruzadas:

- **num_threads** cláusula, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.

- **omp_set_num_threads ()** de función, vea [sección 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) en la página 36.

- **omp_set_dynamic ()** de función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.