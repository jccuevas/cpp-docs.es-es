---
title: OMP_NUM_THREADS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NUM_THREADS
dev_langs: C++
helpviewer_keywords: OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5f6af2ff547ddb95b6d4ef6b9c6d353399c17c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `num`  
 El número máximo de subprocesos que desee en la región paralela, hasta 64 en la implementación de Visual C++.  
  
## <a name="remarks"></a>Comentarios  
 El **OMP_NUM_THREADS** variable de entorno puede reemplazarse por la [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) función o por [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 El valor predeterminado de `num` en Visual C++, implementación de la norma de OpenMP es el número de procesadores virtuales, incluido el hyperthreading CPU.  
  
 Para obtener más información, consulte [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## <a name="example"></a>Ejemplo  
 El comando siguiente establece la **OMP_NUM_THREADS** variable de entorno a 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 El comando siguiente muestra la configuración actual de la **OMP_NUM_THREADS** variable de entorno:  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>Vea también  
 [Variables de entorno](../../../parallel/openmp/reference/openmp-environment-variables.md)