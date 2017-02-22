---
title: "omp_destroy_nest_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_destroy_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_destroy_nest_lock OpenMP function"
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# omp_destroy_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

desinicializa un bloqueo encajable.  
  
## Sintaxis  
  
```  
void omp_destroy_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) cuyas se inicializó con [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## Comentarios  
 Para obtener más información, vea [3.2.2 omp\_destroy\_lock and omp\_destroy\_nest\_lock Functions](../Topic/3.2.2%20omp_destroy_lock%20and%20omp_destroy_nest_lock%20Functions.md).  
  
## Ejemplo  
 Vea [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo de `omp_destroy_nest_lock`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)