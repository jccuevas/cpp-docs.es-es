---
title: "omp_set_nest_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_nest_lock OpenMP function"
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# omp_set_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Los bloques muestra la ejecución hasta que un bloqueo esté disponible.  
  
## Sintaxis  
  
```  
void omp_set_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) cuyas se inicializó con [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## Comentarios  
 Para obtener más información, vea [3.2.3 omp\_set\_lock and omp\_set\_nest\_lock Functions](../Topic/3.2.3%20omp_set_lock%20and%20omp_set_nest_lock%20Functions.md).  
  
## Ejemplos  
 Vea [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo de `omp_set_nest_lock`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)