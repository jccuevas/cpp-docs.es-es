---
title: num_threads | Microsoft Docs
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
ms.openlocfilehash: d3485d534cf279863b241abcd26195cdde7fea19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016291"
---
# <a name="numthreads"></a>num_threads
Establece el número de subprocesos en un equipo de subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
num_threads(num)  
```  
  
### <a name="parameters"></a>Parámetros
  
*num*<br/>
El número de subprocesos  
  
## <a name="remarks"></a>Comentarios  
 El `num_threads` cláusula tiene la misma funcionalidad que el [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) función.  
  
 `num_threads` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.3 parallel (construcción)](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte [paralelo](../../../parallel/openmp/reference/parallel.md) para obtener un ejemplo del uso de `num_threads` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)