---
title: "num_threads | Microsoft Docs"
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
  - "num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_threads OpenMP clause"
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Establece el número de subprocesos en un equipo de subproceso.  
  
## Sintaxis  
  
```  
num_threads(num)  
```  
  
## Comentarios  
 donde  
  
 `num`  
 el número de subprocesos  
  
## Comentarios  
 la cláusula de `num_threads` tiene la misma funcionalidad que la función de [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) .  
  
 `num_threads` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, vea [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## Ejemplo  
 Vea [parallel](../../../parallel/openmp/reference/parallel.md) para obtener un ejemplo de la cláusula de `num_threads` mediante.  
  
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)