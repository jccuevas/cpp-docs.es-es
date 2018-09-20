---
title: 3.2.4 omp_unset_lock y omp_unset_nest_lock funciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426ac0a5ff974e486f70eed2965fdc27d5acc941
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419118"
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