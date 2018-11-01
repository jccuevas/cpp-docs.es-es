---
title: 3.2.5 omp_test_lock y omp_test_nest_lock (Funciones)
ms.date: 11/04/2016
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
ms.openlocfilehash: e8e03699f807f23f139075560592d8846467f2c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512758"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock y omp_test_nest_lock (Funciones)

Estas funciones intentan establecer un bloqueo, pero no impiden la ejecución del subproceso. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

El argumento debe apuntar a una variable inicializada de bloqueo. Estas funciones intentan establecer un bloqueo en la misma manera que `omp_set_lock` y `omp_set_nest_lock`, salvo que no bloquean la ejecución del subproceso.

Para obtener un bloqueo simple, el `omp_test_lock` función devuelve un valor distinto de cero si el bloqueo se ha establecido correctamente; en caso contrario, devuelve cero.

Para obtener un bloqueo anidable, el `omp_test_nest_lock` función devuelve el nuevo recuento de anidamiento, si se estableció correctamente el bloqueo; en caso contrario, devuelve cero.