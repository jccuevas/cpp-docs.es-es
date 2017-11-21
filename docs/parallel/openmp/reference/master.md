---
title: principal | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: master
dev_langs: C++
helpviewer_keywords: master OpenMP directive
ms.assetid: 559ed974-e02a-486e-a23f-31556429b2c4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 405c5f6cfba3ab60abac30fdb8a0ac730f1ab8b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="master"></a>master
Especifica que sólo lo threadshould maestro ejecutará una sección del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp master  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>Comentarios  
 El **maestro** directiva es compatible con ningún cláusulas de OpenMP.  
  
 El [único](../../../parallel/openmp/reference/single.md) directiva permite especificar que una sección de código debe ejecutarse en un solo subproceso, no necesariamente el subproceso principal.  
  
 Para obtener más información, consulte [2.6.1 master construcción](../../../parallel/openmp/2-6-1-master-construct.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_master.cpp  
// compile with: /openmp   
#include <omp.h>  
#include <stdio.h>  
  
int main( )   
{  
    int a[5], i;  
  
    #pragma omp parallel  
    {  
        // Perform some computation.  
        #pragma omp for  
        for (i = 0; i < 5; i++)  
            a[i] = i * i;  
  
        // Print intermediate results.  
        #pragma omp master  
            for (i = 0; i < 5; i++)  
                printf_s("a[%d] = %d\n", i, a[i]);  
  
        // Wait.  
        #pragma omp barrier  
  
        // Continue with the computation.  
        #pragma omp for  
        for (i = 0; i < 5; i++)  
            a[i] += i;  
    }  
}  
```  
  
```Output  
a[0] = 0  
a[1] = 1  
a[2] = 4  
a[3] = 9  
a[4] = 16  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)