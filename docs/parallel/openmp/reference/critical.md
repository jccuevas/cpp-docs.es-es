---
title: "critical | Microsoft Docs"
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
  - "Critical"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "critical OpenMP directive"
ms.assetid: 2ab87d6d-5ca4-43ae-9f0a-1f517a6a2bab
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# critical
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que es el código se ejecuta sólo en un subproceso cada vez.  
  
## Sintaxis  
  
```  
#pragma omp critical [(name)]  
{  
   code_block  
}  
```  
  
## Comentarios  
 donde  
  
 \(`name`\) \(opcional\)  
 un nombre para identificar el código crítico.  Observe que el nombre se debe agregar entre paréntesis.  
  
## Comentarios  
 la directiva de **Crtico** no admite ninguna cláusula de OpenMP.  
  
 Para obtener más información, vea [2.6.2 critical Construct](../../../parallel/openmp/2-6-2-critical-construct.md).  
  
## Ejemplo  
  
```  
// omp_critical.cpp  
// compile with: /openmp   
#include <omp.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
#define SIZE 10  
  
int main()   
{  
    int i;  
    int max;  
    int a[SIZE];  
  
    for (i = 0; i < SIZE; i++)   
    {  
        a[i] = rand();  
        printf_s("%d\n", a[i]);  
    }  
  
    max = a[0];  
    #pragma omp parallel for num_threads(4)  
        for (i = 1; i < SIZE; i++)   
        {  
            if (a[i] > max)  
            {  
                #pragma omp critical  
                {  
                    // compare a[i] and max again because max   
                    // could have been changed by another thread after   
                    // the comparison outside the critical section  
                    if (a[i] > max)  
                        max = a[i];  
                }  
            }  
        }  
  
    printf_s("max = %d\n", max);  
}  
```  
  
  **41**  
**18467**  
**6334**  
**26500**  
**19169**  
**15724**  
**11478**  
**29358**  
**26962**  
**24464**  
**\= 29358 máximos**   
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)