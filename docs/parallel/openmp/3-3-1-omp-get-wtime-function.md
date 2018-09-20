---
title: 3.3.1 omp_get_wtime (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec022e9c7e27c848ef535481993dd18dc45f695
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430779"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime (Función)

El `omp_get_wtime` función devuelve un valor de punto flotante de precisión doble igual que el tiempo de reloj transcurrido en segundos desde alguna "hora del pasado".  El "tiempo real en el pasado" es arbitrario, pero se garantiza que no cambian durante la ejecución de la aplicación. El formato es como se detalla a continuación:

```
#include <omp.h>
double omp_get_wtime(void);
```

Se prevé que se utilizará la función para medir los tiempos transcurridos tal como se muestra en el ejemplo siguiente:

```
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Los tiempos de devueltos son "tiempos de cada subproceso" por lo que es significaba que no tienen que ser globalmente coherente en todos los subprocesos que participan en una aplicación.