---
title: num_threads | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7dd57950d083c4f89ee2aa5962ad1e07a55a9a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="numthreads"></a>num_threads
Establece el número de subprocesos en un equipo de subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
num_threads(num)  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `num`  
 El número de subprocesos  
  
## <a name="remarks"></a>Comentarios  
 El `num_threads` cláusula tiene la misma funcionalidad que la [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) (función).  
  
 `num_threads` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.3 parallel (construcción)](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [paralelo](../../../parallel/openmp/reference/parallel.md) para obtener un ejemplo del uso de `num_threads` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)