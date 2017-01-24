---
title: "omp_unset_nest_lock | Microsoft Docs"
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
  - "omp_unset_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_unset_nest_lock OpenMP function"
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_unset_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Libere un bloqueo encajable.  
  
## Sintaxis  
  
```  
void omp_unset_nest_lock(   
   omp_nest_lock_t *lock   
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) cuyas se inicializó con [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md), propiedad el subproceso y ejecuta en la función.  
  
## Comentarios  
 Para obtener más información, vea [3.2.4 omp\_unset\_lock and omp\_unset\_nest\_lock Functions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## Ejemplo  
 Vea [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) para obtener un ejemplo de `omp_unset_nest_lock`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)