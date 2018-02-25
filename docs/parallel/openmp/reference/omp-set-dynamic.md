---
title: omp_set_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00ee1ad4c42e0d2f1303854cbd050e5601d0c3cd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
Indica que el número de subprocesos disponibles en la región paralela posterior puede ser ajustado por el tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `val`  
 Un valor que indica si el número de subprocesos disponibles en la región paralela posterior puede ser ajustado por el tiempo de ejecución.  Si es distinto de cero, que el tiempo de ejecución puede ajustar el número de subprocesos, si es cero, el tiempo de ejecución no ajustará dinámicamente el número de subprocesos.  
  
## <a name="remarks"></a>Comentarios  
 El número de subprocesos nunca superará el valor establecido por [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) o [OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
 Use [omp_get_dynamic ()](../../../parallel/openmp/reference/omp-get-dynamic.md) para mostrar la configuración actual de `omp_set_dynamic`.  
  
 La configuración de `omp_set_dynamic` sobrescribirá la configuración de la [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) variable de entorno.  
  
 Para obtener más información, consulte [3.1.7 omp_set_dynamic (función)](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)