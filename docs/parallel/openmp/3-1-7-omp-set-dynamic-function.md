---
title: 3.1.7 omp_set_dynamic (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 807e5739c571f7aa8e9f723a0a48c8c46f1e6d09
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441569"
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic (Función)

El **omp_set_dynamic ()** función habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de las regiones en paralelo. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* se evalúa como un valor distinto de cero, se puede ajustar el número de subprocesos que se utilizan para ejecutar las siguientes regiones en paralelo automáticamente por el entorno de tiempo de ejecución para usar mejor los recursos del sistema. Como consecuencia, el número de subprocesos especificados por el usuario es el número máximo de subprocesos. El número de subprocesos en el equipo de ejecución de una región paralela permanece fijo para la duración de esa región paralela y notifica el **omp_get_num_threads ()** función.

Si *dynamic_threads* se evalúa como 0, se deshabilita el ajuste dinámico.

Esta función tiene los efectos que se ha descrito anteriormente, cuando se llama desde una parte del programa donde el **omp_in_parallel ()** función devuelve cero. Si se llama desde una parte del programa donde el **omp_in_parallel ()** función devuelve un valor distinto de cero, el comportamiento de esta función es indefinido.

Una llamada a **omp_set_dynamic ()** tiene prioridad sobre la **OMP_DYNAMIC** variable de entorno.

El valor predeterminado para el ajuste dinámico de subprocesos es definido por la implementación. Como resultado, los códigos de usuario que dependen de un número específico de subprocesos para su ejecución correcta, deben deshabilitarse subprocesos dinámicos. Las implementaciones no son necesarias para proporcionar la capacidad de ajustar dinámicamente el número de subprocesos, pero son necesarias para proporcionar la interfaz con el fin de admitir la portabilidad entre todas las plataformas.

## <a name="cross-references"></a>Referencias cruzadas:

- **omp_get_num_threads ()** de función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.

- **OMP_DYNAMIC** vea variable de entorno [sección 4.3](../../parallel/openmp/4-3-omp-dynamic.md) en la página 49.

- **omp_in_parallel ()** de función, vea [sección 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) en página 38.