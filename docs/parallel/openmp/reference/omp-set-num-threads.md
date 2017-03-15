---
title: "omp_set_num_threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_num_threads OpenMP function"
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# omp_set_num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Establece el número de subprocesos en regiones paralelas posteriores, a menos que se reemplace con una cláusula de [num\_threads](../../../parallel/openmp/reference/num-threads.md) .  
  
## Sintaxis  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## Comentarios  
 donde  
  
 `num_threads`  
 El número de subprocesos de la región paralela.  
  
## Comentarios  
 Para obtener más información, vea [3.1.1 omp\_set\_num\_threads Function](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## Ejemplo  
 Vea [omp\_get\_num\_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) para obtener un ejemplo de `omp_set_num_threads`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)