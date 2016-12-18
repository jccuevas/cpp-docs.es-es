---
title: "if (OpenMP) | Microsoft Docs"
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
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "if OpenMP clause"
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# if (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica si un bucle se debe ejecutar en paralelo o en serie.  
  
## Sintaxis  
  
```  
if(expression)  
```  
  
## Comentarios  
 donde  
  
 `expression`  
 Una expresión entera que, si se evalúa como true \(cero\), hace que el código de la región paralela para ejecutarse en paralelo.  Si la expresión se evalúa en false \(cero\), la región paralela se ejecuta en serie \(por un subproceso\).  
  
## Comentarios  
 `if` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, vea [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## Ejemplo  
  
```  
// omp_if.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
void test(int val)  
{  
    #pragma omp parallel if (val)  
    if (omp_in_parallel())  
    {  
        #pragma omp single  
        printf_s("val = %d, parallelized with %d threads\n",  
                 val, omp_get_num_threads());  
    }  
    else  
    {  
        printf_s("val = %d, serialized\n", val);  
    }  
}  
  
int main( )  
{  
    omp_set_num_threads(2);  
    test(0);  
    test(2);  
}  
```  
  
  **\= 0 val, serializado**  
**\= 2 val, en paralelo con 2 subprocesos**   
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)