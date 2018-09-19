---
title: OMP_NUM_THREADS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NUM_THREADS
dev_langs:
- C++
helpviewer_keywords:
- OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39f45b9c81d5339b2b6afe4c77fdc9bac6b5d731
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091171"
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
### <a name="parameters"></a>Parámetros
  
*num*<br/>
El número máximo de subprocesos que desee en la región paralela, hasta 64 en la implementación de Visual C++.  
  
## <a name="remarks"></a>Comentarios  
 El **OMP_NUM_THREADS** variable de entorno puede reemplazarse por la [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) función o por [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 El valor predeterminado de `num` en Visual C++ implementación del estándar OpenMP es el número de procesadores virtuales, incluidas las CPU de hyperthreading.  
  
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