---
title: 3.1.4 omp_get_thread_num (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a21a682c051daffde16b3d5cfc63fd2d679c4de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444923"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num (Función)

El `omp_get_thread_num` función devuelve el número de subprocesos dentro de su equipo, del subproceso que ejecuta la función. Los archivos de número de subproceso entre 0 y **omp_get_num_threads()**-1, ambos inclusive. El subproceso principal del equipo es 0.

El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_thread_num(void);
```

Si se llama desde una región de la serie, `omp_get_thread_num` devuelve 0. Si se llama desde dentro de una región paralela anidada que se serializa, esta función devuelve 0.

## <a name="cross-references"></a>Referencias cruzadas:

- `omp_get_num_threads` función, vea [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37.