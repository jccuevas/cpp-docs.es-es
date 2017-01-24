---
title: "omp_get_dynamic | Microsoft Docs"
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
  - "omp_get_dynamic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_dynamic OpenMP function"
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_get_dynamic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Devuelve un valor que indica si el número de subprocesos disponibles en la región paralela subsiguiente se puede ajustar el motor en tiempo de ejecución.  
  
## Sintaxis  
  
```  
int omp_get_dynamic();  
```  
  
## Valor devuelto  
 Si es distinto de cero, el ajuste dinámico de subprocesos está habilitada.  
  
## Comentarios  
 el ajuste dinámico de subprocesos se especifica con [omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) y [OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).  
  
 Para obtener más información, vea [3.1.7 omp\_set\_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## Ejemplo  
 Vea [omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) para obtener un ejemplo de `omp_get_dynamic`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)