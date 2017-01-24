---
title: "A.5   Using the critical Directive | Microsoft Docs"
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
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.5   Using the critical Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el ejemplo siguiente incluye varias directivas de `critical` \([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18\).  El ejemplo muestra un modelo de puesta en cola en el que una tarea dequeued y se funcione.  Para protegerse de varios subprocesos dequeuing la misma tarea, la operación dequeuing debe estar en una sección de `critical` .  Dado que las dos colas de este ejemplo son independientes, están protegidas por las directivas de `critical` con nombres diferentes, *xaxis* y *yaxis*.  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```