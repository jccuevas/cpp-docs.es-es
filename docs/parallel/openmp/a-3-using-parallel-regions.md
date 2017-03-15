---
title: "A.3   Using Parallel Regions | Microsoft Docs"
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
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.3   Using Parallel Regions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de `parallel` \([sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8\) se puede utilizar en programas del código grueso\-grano.  En el ejemplo siguiente, cada subproceso de la región paralela decide en qué parte de la matriz global `x` funcionen, según el número de subprocesos:  
  
```  
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)  
{  
    iam = omp_get_thread_num();  
    np =  omp_get_num_threads();  
    ipoints = npoints / np;  
    subdomain(x, iam, ipoints);  
}  
```