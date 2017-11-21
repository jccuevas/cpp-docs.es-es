---
title: omp_lock_t | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_lock_t
dev_langs: C++
helpviewer_keywords: omp_lock_t OpenMP data type
ms.assetid: 51b80629-4ffc-4b8a-95c7-1af048f1f286
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 764ce81ca11a1998914cd6d1ea38612afde28936
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="omplockt"></a>omp_lock_t
Un tipo que contiene el estado de un bloqueo, si el bloqueo está disponible o si un subproceso mantiene un bloqueo.  
  
 Los siguientes funciones utilizan **omp_lock_t**:  
  
-   [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)  
  
-   [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)  
  
-   [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)  
  
-   [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)  
  
-   [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)  
  
 Para obtener más información, consulte [3.2 funciones de bloqueo](../../../parallel/openmp/3-2-lock-functions.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) para obtener un ejemplo del uso de **omp_lock_t**.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos](../../../parallel/openmp/reference/openmp-data-types.md)