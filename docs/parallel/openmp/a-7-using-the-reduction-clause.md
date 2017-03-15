---
title: "A.7   Using the reduction Clause | Microsoft Docs"
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
ms.assetid: e71e65bc-a25c-4f02-b507-66b52bf950a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.7   Using the reduction Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ejemplo siguiente se muestra la cláusula reduction \([sección 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) en la página 28\):  
  
```  
#pragma omp parallel for private(i) shared(x, y, n) \  
                         reduction(+: a, b)  
    for (i=0; i<n; i++) {  
        a = a + x[i];  
        b = b + y[i];  
    }  
```