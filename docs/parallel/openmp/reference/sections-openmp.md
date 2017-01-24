---
title: "sections (OpenMP) | Microsoft Docs"
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
  - "section"
  - "SECTIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sections OpenMP directive"
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sections (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

identifica las secciones de código que se dividirán entre todos los subprocesos.  
  
## Sintaxis  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## Comentarios  
 donde  
  
 `clause` \(opcional\)  
 cero o más cláusula.  Vea la sección comentarios para obtener una lista de las cláusulas admitidas por **secciones**.  
  
## Comentarios  
 la directiva de **secciones** puede contener cero o más directiva de **sección** .  
  
 La directiva de **secciones** admite las siguientes cláusulas de OpenMP:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 si **Paralelo** también se especifica, `clause` puede ser cualquier cláusula aceptada por las directivas de **Paralelo** o de **secciones** , excepto `nowait`.  
  
 Para obtener más información, vea [2.4.2 sections Construct](../../../parallel/openmp/2-4-2-sections-construct.md).  
  
## Ejemplo  
  
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
  
  **Hello de subproceso 0**  
**Hello de subproceso 0**   
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)