---
title: "omp_lock_t | Microsoft Docs"
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
  - "omp_lock_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_lock_t OpenMP data type"
ms.assetid: 51b80629-4ffc-4b8a-95c7-1af048f1f286
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_lock_t
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un tipo que contiene el estado de un bloqueo, si el bloqueo está disponible o si un subproceso posee un bloqueo.  
  
 El uso siguiente **omp\_lock\_t**de funciones:  
  
-   [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)  
  
-   [omp\_destroy\_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)  
  
-   [omp\_set\_lock](../../../parallel/openmp/reference/omp-set-lock.md)  
  
-   [omp\_unset\_lock](../../../parallel/openmp/reference/omp-unset-lock.md)  
  
-   [omp\_test\_lock](../../../parallel/openmp/reference/omp-test-lock.md)  
  
 Para obtener más información, vea [3.2 Lock Functions](../../../parallel/openmp/3-2-lock-functions.md).  
  
## Ejemplo  
 Vea [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md) para obtener un ejemplo de **omp\_lock\_t**mediante.  
  
## Vea también  
 [Data Types](../../../parallel/openmp/reference/openmp-data-types.md)