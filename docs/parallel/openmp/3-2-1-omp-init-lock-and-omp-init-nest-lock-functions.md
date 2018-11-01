---
title: 3.2.1 omp_init_lock y omp_init_nest_lock (Funciones)
ms.date: 11/04/2016
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
ms.openlocfilehash: 2d15aacb5e6743d18150fb45bea85b7ca22a401f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472785"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock y omp_init_nest_lock (Funciones)

Estas funciones proporcionan el único medio de inicializar un bloqueo. Cada función inicializa el bloqueo asociado al parámetro *bloqueo* para su uso en las llamadas posteriores. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Se desbloquea el estado inicial (es decir, no hay ningún subproceso posee el bloqueo). Un bloqueo anidable, el recuento inicial de anidamiento es cero. No es conforme al llamar a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.