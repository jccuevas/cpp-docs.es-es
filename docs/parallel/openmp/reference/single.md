---
title: "single | Microsoft Docs"
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
  - "Single"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single OpenMP directive"
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# single
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Permite especificar que una sección de código debe ejecutarse en un subproceso, no necesariamente el subproceso principal.  
  
## Sintaxis  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### Parámetros  
 `clause` \(opcional\)  
 cero o más cláusula.  Vea la sección comentarios para obtener una lista de las cláusulas admitidas por **solo**.  
  
## Comentarios  
 La directiva de **solo** admite las siguientes cláusulas de OpenMP:  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 La directiva de [master](../../../parallel/openmp/reference/master.md) permite especificar que una sección de código se debe ejecutar solo en el subproceso principal.  
  
 Para obtener más información, vea [2.4.3 single Construct](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## Ejemplo  
  
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
  
  **entrada de lectura**  
**resultado del cálculo**  
**resultado del cálculo**  
**salida de escritura**   
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)