---
title: "A.18   Nested for Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ae2b2e0b-ec94-43f8-928c-6d621b51f0df
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.18   Nested for Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El siguiente ejemplo de anidamiento de directivas de `for` \([sección 2,9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33\) es bajo porque las directivas internas y externas de `for` enlazan a diferentes regiones paralelas:  
  
```  
#pragma omp parallel default(shared)  
{  
    #pragma omp for  
        for (i=0; i<n; i++)   
        {  
            #pragma omp parallel shared(i, n)  
            {  
                #pragma omp for  
                    for (j=0; j<n; j++)  
                        work(i, j);  
            }  
        }  
}  
```  
  
 Una variación siguiente del ejemplo anterior es también bajo:  
  
```  
#pragma omp parallel default(shared)  
{  
    #pragma omp for  
        for (i=0; i<n; i++)  
            work1(i, n);  
}  
  
void work1(int i, int n)  
{  
    int j;  
    #pragma omp parallel default(shared)  
    {  
        #pragma omp for  
            for (j=0; j<n; j++)  
                work2(i, j);  
    }  
    return;  
}  
```