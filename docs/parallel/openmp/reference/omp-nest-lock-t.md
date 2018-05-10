---
title: omp_nest_lock_t | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- omp_nest_lock_t OpenMP data type
ms.assetid: fceac9fb-96d2-42b0-af19-c9b078380618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c47581e2587ea7c82ff3b84ad41d0c83d1659b7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ompnestlockt"></a>omp_nest_lock_t
Un tipo que contiene las siguientes partes de información sobre un bloqueo: si el bloqueo está disponible y la identidad del subproceso que posee el bloqueo y un recuento de anidamiento.  
  
 Los siguientes funciones utilizan **omp_nest_lock_t**:  
  
-   [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)  
  
-   [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)  
  
-   [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)  
  
-   [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)  
  
-   [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)  
  
 Para obtener más información, consulte [3.2 funciones de bloqueo](../../../parallel/openmp/3-2-lock-functions.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo del uso de **omp_nest_lock_t**.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos](../../../parallel/openmp/reference/openmp-data-types.md)