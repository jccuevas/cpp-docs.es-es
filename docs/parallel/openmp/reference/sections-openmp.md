---
title: secciones (OpenMP) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- section
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60bc94685a7e6128e22cc3545ae8702abe6d472e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="sections-openmp"></a>sections (OpenMP)
Identifica las secciones de código para ser dividido entre todos los subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `clause` (opcional)  
 Cero o más cláusulas. Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con **secciones**.  
  
## <a name="remarks"></a>Comentarios  
 El **secciones** directiva puede contener cero o más **sección** directivas.  
  
 El **secciones** directiva es compatible con las cláusulas de OpenMP siguientes:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 Si **paralelo** también se especifica, `clause` cualquier cláusula puede ser aceptado por la **paralelo** o **secciones** directivas, excepto `nowait`.  
  
 Para obtener más información, consulte [2.4.2 sections (construcción)](../../../parallel/openmp/2-4-2-sections-construct.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_sections.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
    #pragma omp parallel sections num_threads(4)  
    {  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
        #pragma omp section  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
    }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 0  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)