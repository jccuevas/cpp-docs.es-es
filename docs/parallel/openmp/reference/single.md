---
title: solo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Single
dev_langs:
- C++
helpviewer_keywords:
- single OpenMP directive
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff1a255933b79d39b6eedbb9362ff76a34e0f8a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716994"
---
# <a name="single"></a>única
Le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente el subproceso principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### <a name="parameters"></a>Parámetros  

`clause`  
(Opcional) Cero o más cláusulas. Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con **único**.  
  
## <a name="remarks"></a>Comentarios  
 El **único** directiva es compatible con las cláusulas de OpenMP siguientes:  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 El [maestro](../../../parallel/openmp/reference/master.md) directiva le permite especificar que una sección de código debe ejecutarse solo en el subproceso principal.  
  
 Para obtener más información, consulte [2.4.3 single construir](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
```Output  
read input  
compute results  
compute results  
write output  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)