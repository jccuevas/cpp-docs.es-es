---
title: "master | Microsoft Docs"
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
  - "master"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "master OpenMP directive"
ms.assetid: 559ed974-e02a-486e-a23f-31556429b2c4
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# master
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que sólo el threadshould principal ejecuta una sección del programa.  
  
## Sintaxis  
  
```  
#pragma omp master  
{  
   code_block  
}  
```  
  
## Comentarios  
 la directiva de **principal** no admite ninguna cláusula de OpenMP.  
  
 La directiva de [single](../../../parallel/openmp/reference/single.md) permite especificar que una sección de código debe ejecutarse en un subproceso, no necesariamente el subproceso principal.  
  
 Para obtener más información, vea [2.6.1 master Construct](../../../parallel/openmp/2-6-1-master-construct.md).  
  
## Ejemplo  
  
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
  
  **a \[0\] \= 0**  
**a \[1\] \= 1**  
**a \[2\] \= 4**  
**a \[3\] \= 9**  
**a \[4\] \= 16**   
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)