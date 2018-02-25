---
title: ordenada (directivas de OpenMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ordered
dev_langs:
- C++
helpviewer_keywords:
- ordered OpenMP directive
ms.assetid: e1aa703e-d07d-4f6a-9b2a-f4f25203d850
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: def203120826d78481956b0efbde8831d624a4ce
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ordered-openmp-directives"></a>ordered (Directivas de OpenMP)
Especifica que el código en una ejecución en paralelo para bucle debe ejecutarse como un bucle secuencial.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp ordered  
   structured-block  
```  
  
## <a name="remarks"></a>Comentarios  
 El **ordenados** directiva debe estar en la extensión dinámica de un [para](../../../parallel/openmp/reference/for-openmp.md) o **for paralelos** construir con un **ordenados** cláusula.  
  
 El **ordenados** directiva es compatible con ningún cláusulas de OpenMP.  
  
 Para obtener más información, consulte [2.6.6 ordered (construcción)](../../../parallel/openmp/2-6-6-ordered-construct.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_ordered.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
static float a[1000], b[1000], c[1000];  
  
void test(int first, int last)   
{  
    #pragma omp for schedule(static) ordered  
    for (int i = first; i <= last; ++i) {  
        // Do something here.  
        if (i % 2)   
        {  
            #pragma omp ordered   
            printf_s("test() iteration %d\n", i);  
        }  
    }  
}  
  
void test2(int iter)   
{  
    #pragma omp ordered  
    printf_s("test2() iteration %d\n", iter);  
}  
  
int main( )   
{  
    int i;  
    #pragma omp parallel  
    {  
        test(1, 8);  
        #pragma omp for ordered  
        for (i = 0 ; i < 5 ; i++)  
            test2(i);  
    }  
}  
```  
  
```Output  
test() iteration 1  
test() iteration 3  
test() iteration 5  
test() iteration 7  
test2() iteration 0  
test2() iteration 1  
test2() iteration 2  
test2() iteration 3  
test2() iteration 4  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)