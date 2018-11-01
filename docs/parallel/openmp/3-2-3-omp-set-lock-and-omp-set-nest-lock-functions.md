---
title: 3.2.3 omp_set_lock y omp_set_nest_lock funciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 792b95baef2821bb693d9a90fc228d2b0c508e1f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420366"
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