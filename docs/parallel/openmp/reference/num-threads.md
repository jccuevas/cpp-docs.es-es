---
title: num_threads | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: num_threads
dev_langs: C++
helpviewer_keywords: num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7289a843c33fbc9ba23d6006997dea8e09ba7c79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 `num_threads`se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.3 parallel (construcción)](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [paralelo](../../../parallel/openmp/reference/parallel.md) para obtener un ejemplo del uso de `num_threads` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)