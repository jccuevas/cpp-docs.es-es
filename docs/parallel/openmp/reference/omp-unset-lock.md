---
title: "omp_unset_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_unset_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_unset_lock OpenMP function"
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# omp_unset_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Libere un bloqueo.  
  
## Sintaxis  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) cuyas se inicializó con [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md), propiedad el subproceso y ejecuta en la función.  
  
## Comentarios  
 Para obtener más información, vea [3.2.4 omp\_unset\_lock and omp\_unset\_nest\_lock Functions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## Ejemplo  
 Vea [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md) para obtener un ejemplo de `omp_unset_lock`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)