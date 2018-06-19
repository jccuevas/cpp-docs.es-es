---
title: omp_set_num_threads () | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 335cb283026a019d6c6a03565c5dbec541140db3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691318"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Establece el número de subprocesos en regiones posteriores en paralelo, a menos que se reemplaza por un [num_threads](../../../parallel/openmp/reference/num-threads.md) cláusula.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `num_threads`  
 El número de subprocesos en la región paralela.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [3.1.1 omp_set_num_threads (función)](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_get_num_threads ()](../../../parallel/openmp/reference/omp-get-num-threads.md) para obtener un ejemplo del uso de `omp_set_num_threads`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)