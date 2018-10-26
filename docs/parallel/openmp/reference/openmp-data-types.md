---
title: Tipos de datos de OpenMP | Microsoft Docs
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
ms.openlocfilehash: 97cf6ccad0a3b30c0abfa0076ea9c6a30b205d67
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065205"
---
# <a name="openmp-data-types"></a>Tipos de datos de OpenMP

Proporciona vínculos a los tipos de datos utilizados en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye los siguientes tipos de datos.

|Tipo de datos|Descripción|
|---------|-----------|
|[omp_lock_t](#omp-lock-t)|Un tipo que contiene el estado de un bloqueo, si el bloqueo esté disponible o si un subproceso posee un bloqueo.|
|[omp_nest_lock_t](#omp-nest-lock-t)|Un tipo que contiene uno de los siguientes fragmentos de información sobre un bloqueo: si el bloqueo esté disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.|

## <a name="omp-lock-t"></a>omp_lock_t

Un tipo que contiene el estado de un bloqueo, si el bloqueo esté disponible o si un subproceso posee un bloqueo.

Los siguientes funciones utilizan `omp_lock_t`:

- [omp_init_lock](openmp-functions.md#omp-init-lock)
- [omp_destroy_lock](openmp-functions.md#omp-destroy-lock)
- [omp_set_lock](openmp-functions.md#omp-set-lock)
- [omp_unset_lock](openmp-functions.md#omp-unset-lock)
- [omp_test_lock](openmp-functions.md#omp-test-lock)

Para obtener más información, consulte [3.2 funciones de bloqueo](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_lock](openmp-functions.md#omp-init-lock) para obtener un ejemplo del uso de `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

Un tipo que contiene los siguientes fragmentos de información sobre un bloqueo: si el bloqueo esté disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.

Los siguientes funciones utilizan `omp_nest_lock_t`:

- [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)
- [omp_destroy_nest_lock](openmp-functions.md#omp-destroy-nest-lock)
- [omp_set_nest_lock](openmp-functions.md#omp-set-nest-lock)
- [omp_unset_nest_lock](openmp-functions.md#omp-unset-nest-lock)
- [omp_test_nest_lock](openmp-functions.md#omp-test-nest-lock)

Para obtener más información, consulte [3.2 funciones de bloqueo](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Ejemplo

Consulte [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock) para obtener un ejemplo del uso de `omp_nest_lock_t`.
