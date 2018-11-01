---
title: 3.3.1 omp_get_wtime (Función)
ms.date: 11/04/2016
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
ms.openlocfilehash: 544a1bc9a613a2888cb7c5e68e54fdfae1b1c333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460572"
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