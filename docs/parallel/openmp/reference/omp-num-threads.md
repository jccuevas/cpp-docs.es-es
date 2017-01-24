---
title: "OMP_NUM_THREADS | Microsoft Docs"
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
  - "OMP_NUM_THREADS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_NUM_THREADS OpenMP environment variable"
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OMP_NUM_THREADS
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Establece el número máximo de subprocesos de la región paralela, a menos que se reemplace con [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num\_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## Sintaxis  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## Comentarios  
 donde  
  
 `num`  
 El número máximo de subprocesos que desee de la región paralela, hasta 64 en la implementación de Visual C\+\+.  
  
## Comentarios  
 La variable de entorno **OMP\_NUM\_THREADS** puede reemplazarse por la función de [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) o por [num\_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 El valor predeterminado de `num` en la implementación de Visual C\+\+ del estándar de OpenMP es el número de procesadores virtuales, incluidos hyperthreading CPU.  
  
 Para obtener más información, vea [4.2 OMP\_NUM\_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## Ejemplo  
 El comando siguiente establece la variable de entorno **OMP\_NUM\_THREADS** a 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 El comando siguiente muestra la configuración actual de la variable de entorno **OMP\_NUM\_THREADS** :  
  
```  
set OMP_NUM_THREADS  
```  
  
## Vea también  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)