---
title: "parallel | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "parallel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parallel OpenMP directive"
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# parallel
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Define una región paralela, que es el código que se ejecutará por varios subprocesos en paralelo.  
  
## Sintaxis  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## Comentarios  
 donde  
  
 `clause` \(opcional\)  
 cero o más cláusula.  Vea la sección comentarios para obtener una lista de las cláusulas admitidas por **Paralelo**.  
  
## Comentarios  
 La directiva de **Paralelo** admite las siguientes cláusulas de OpenMP:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num\_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [shared](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **Paralelo** también se puede utilizar con las directivas de [sections](../../../parallel/openmp/reference/sections-openmp.md) y de [for](../../../parallel/openmp/reference/for-openmp.md) .  
  
 Para obtener más información, vea [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo establecer el número de subprocesos y definir una región paralela.  De forma predeterminada, el número de subprocesos es igual al número de procesadores lógicos en el equipo.  Por ejemplo, si tiene un equipo con un procesador físico que tenga hyperthreading habilitado, tendrá dos procesadores lógicos y, por consiguiente, dos subprocesos.  
  
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
  
  **Hello de subproceso 0**  
**Hello de subproceso 1**  
**Hello de subproceso 2**  
**Hello de subproceso 3**   
## Comment  
 Tenga en cuenta que el orden de salida puede variar en equipos diferentes.  
  
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)