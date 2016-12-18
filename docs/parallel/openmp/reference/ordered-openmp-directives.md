---
title: "ordered (OpenMP Directives) | Microsoft Docs"
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
  - "ordered"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordered OpenMP directive"
ms.assetid: e1aa703e-d07d-4f6a-9b2a-f4f25203d850
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ordered (OpenMP Directives)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que el código en paralelo del bucle se debe ejecutar como un bucle secuencial.  
  
## Sintaxis  
  
```  
#pragma omp ordered  
   structured-block  
```  
  
## Comentarios  
 la directiva de **consultar** debe estar dentro de la extensión dinámica de una construcción de [for](../../../parallel/openmp/reference/for-openmp.md) o de **paralelo para** con una cláusula de **consultar** .  
  
 la directiva de **consultar** no admite ninguna cláusula de OpenMP.  
  
 Para obtener más información, vea [2.6.6 ordered Construct](../../../parallel/openmp/2-6-6-ordered-construct.md).  
  
## Ejemplo  
  
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
  
  **probar \(\) la iteración 1**  
**probar \(\) la iteración 3**  
**probar \(\) la iteración 5**  
**probar \(\) la iteración 7**  
**\(\) iteración test2 0**  
**\(\) iteración test2 1**  
**\(\) iteración test2 2**  
**\(\) iteración test2 3**  
**\(\) iteración test2 4**   
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)