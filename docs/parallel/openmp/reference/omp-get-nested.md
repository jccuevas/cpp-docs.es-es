---
title: "omp_get_nested | Microsoft Docs"
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
  - "omp_get_nested"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_nested OpenMP function"
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_get_nested
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Devuelve un valor que indica si se habilita el paralelismo anidados.  
  
## Sintaxis  
  
```  
int omp_get_nested( );  
```  
  
## Valor devuelto  
 Si es distinto de cero, se habilita el paralelismo anidados.  
  
## Comentarios  
 El paralelismo anidados se especifica con [omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md) y [OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md).  
  
 Para obtener más información, vea [3.1.10 omp\_get\_nested Function](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).  
  
## Ejemplo  
 Vea [omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md) para obtener un ejemplo de `omp_get_nested`mediante.  
  
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)