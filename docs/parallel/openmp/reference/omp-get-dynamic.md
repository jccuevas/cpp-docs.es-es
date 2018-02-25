---
title: omp_get_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865104055fc98946c09152f328f4812af0120e64
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
Devuelve un valor que indica si el número de subprocesos disponibles en la región paralela posterior puede ser ajustado por el tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es distinto de cero, realizar un ajuste dinámico de subprocesos está habilitado.  
  
## <a name="remarks"></a>Comentarios  
 Realizar un ajuste dinámico de subprocesos se especifica con [omp_set_dynamic ()](../../../parallel/openmp/reference/omp-set-dynamic.md) y [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).  
  
 Para obtener más información, consulte [3.1.7 omp_set_dynamic (función)](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_set_dynamic ()](../../../parallel/openmp/reference/omp-set-dynamic.md) para obtener un ejemplo del uso de `omp_get_dynamic`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)