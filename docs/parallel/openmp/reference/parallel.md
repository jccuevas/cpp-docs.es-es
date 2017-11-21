---
title: paralelo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: parallel
dev_langs: C++
helpviewer_keywords: parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 289a4928c9c46f6d758ddc2f30ed864488ab725e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="parallel"></a>parallel
Define una región paralela, que es código que se ejecutará por varios subprocesos en paralelo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `clause` (opcional)  
 Cero o más cláusulas.  Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con **paralelo**.  
  
## <a name="remarks"></a>Comentarios  
 El **paralelo** directiva es compatible con las cláusulas de OpenMP siguientes:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [compartido](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **paralelo** también puede usarse con el [secciones](../../../parallel/openmp/reference/sections-openmp.md) y [para](../../../parallel/openmp/reference/for-openmp.md) directivas.  
  
 Para obtener más información, consulte [2.3 parallel (construcción)](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo establecer el número de subprocesos y definir una región paralela. De forma predeterminada, el número de subprocesos es igual al número de procesadores lógicos en el equipo. Por ejemplo, si tiene un equipo con un procesador físico con el hyperthreading habilitado, tendrá dos procesadores lógicos y, por lo tanto, dos subprocesos.  
  
```  
// omp_parallel.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(4)  
   {  
      int i = omp_get_thread_num();  
      printf_s("Hello from thread %d\n", i);  
   }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 1  
Hello from thread 2  
Hello from thread 3  
```  
  
## <a name="comment"></a>Comentario  
 Tenga en cuenta que el orden de salida puede variar en equipos diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)