---
title: 3.2.3 omp_set_lock y omp_set_nest_lock (Funciones)
ms.date: 11/04/2016
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
ms.openlocfilehash: 8efc1f844be2d1b8cf9b15242758914edd0fca14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617664"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock y omp_set_nest_lock (Funciones)

Cada una de estas funciones bloquea el subproceso que ejecuta la función hasta que el bloqueo especificado está disponible y, a continuación, Establece el bloqueo. Un bloqueo simple está disponible si está desbloqueada. Un bloqueo anidable está disponible si está desbloqueada, o si ya tiene propietario por el subproceso que ejecuta la función. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Un bloqueo simple, el argumento para el `omp_set_lock` función debe apuntar a una variable inicializada de bloqueo. La propiedad del bloqueo se concede al subproceso de ejecución de la función.

Un bloqueo anidable, el argumento para el `omp_set_nest_lock` función debe apuntar a una variable inicializada de bloqueo. Se incrementa el recuento de anidamiento, y el subproceso se concede o conserva la propiedad del bloqueo.