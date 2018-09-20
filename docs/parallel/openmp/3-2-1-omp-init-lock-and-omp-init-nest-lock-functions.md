---
title: 3.2.1 omp_init_lock y omp_init_nest_lock funciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4303eb3ccfcb1c449022a4be32f94b9f91e6e80c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387008"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock y omp_init_nest_lock (Funciones)

Estas funciones proporcionan el único medio de inicializar un bloqueo. Cada función inicializa el bloqueo asociado al parámetro *bloqueo* para su uso en las llamadas posteriores. El formato es como se detalla a continuación:

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Se desbloquea el estado inicial (es decir, no hay ningún subproceso posee el bloqueo). Un bloqueo anidable, el recuento inicial de anidamiento es cero. No es conforme al llamar a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.