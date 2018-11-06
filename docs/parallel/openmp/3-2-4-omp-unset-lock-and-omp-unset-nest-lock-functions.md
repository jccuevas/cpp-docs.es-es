---
title: 3.2.4 omp_unset_lock y omp_unset_nest_lock (Funciones)
ms.date: 11/04/2016
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
ms.openlocfilehash: b0764e3590f8edb3a3e783d9b5493a64be154401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607875"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock y omp_unset_nest_lock (Funciones)

Estas funciones proporcionan los medios de liberar la propiedad de un bloqueo. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

El argumento para cada una de estas funciones debe apuntar a una variable inicializada de bloqueo que pertenece al subproceso de ejecución de la función. El comportamiento es indefinido si el subproceso no es el propietario de dicho bloqueo.

Para obtener un bloqueo simple, el `omp_unset_lock` función libera el subproceso que ejecuta la función de la propiedad del bloqueo.

Para obtener un bloqueo anidable, el `omp_unset_nest_lock` función disminuye el recuento de anidamiento y las versiones el subproceso que ejecuta la función de la propiedad del bloqueo, si el recuento resultante es cero.