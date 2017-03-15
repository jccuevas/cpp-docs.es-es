---
title: "omp_set_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_lock OpenMP function"
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# omp_set_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Los bloques muestra la ejecución hasta que un bloqueo esté disponible.  
  
## Sintaxis  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) cuyas se inicializó con [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## Comentarios  
 Para obtener más información, vea [3.2.3 omp\_set\_lock and omp\_set\_nest\_lock Functions](../Topic/3.2.3%20omp_set_lock%20and%20omp_set_nest_lock%20Functions.md).  
  
## Ejemplos  
 Vea [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md) para obtener un ejemplo de `omp_set_lock`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)