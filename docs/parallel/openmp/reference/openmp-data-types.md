---
title: Los tipos de datos de OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 254dffebc258867088f738b10a11bf48d31bd0a4
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990075"
---
# <a name="openmp-data-types"></a>Tipos de datos de OpenMP

Proporciona vínculos a los tipos de datos utilizados en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye los siguientes tipos de datos.

Tipo de datos                           | Descripción
----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[omp_lock_t](#omp-lock-t)           | Un tipo que contiene el estado de un bloqueo, si el bloqueo esté disponible o si un subproceso posee un bloqueo.
[omp_nest_lock_t](#omp-nest-lock-t) | Un tipo que contiene uno de los siguientes fragmentos de información sobre un bloqueo: si el bloqueo esté disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.

## <a name="omp-lock-t"></a>omp_lock_t

Un tipo que contiene el estado de un bloqueo, si el bloqueo esté disponible o si un subproceso posee un bloqueo.

Los siguientes funciones utilizan `omp_lock_t`:

- [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)
- [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)
- [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)
- [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)
- [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)

Para obtener más información, consulte [3.2 funciones de bloqueo](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) para obtener un ejemplo del uso de `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

Un tipo que contiene los siguientes fragmentos de información sobre un bloqueo: si el bloqueo esté disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.

Los siguientes funciones utilizan `omp_nest_lock_t`:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)
- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)
- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)
- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)
- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

Para obtener más información, consulte [3.2 funciones de bloqueo](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo del uso de `omp_nest_lock_t`.
