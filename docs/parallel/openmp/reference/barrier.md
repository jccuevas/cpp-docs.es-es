---
title: "barrier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "barrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "barrier OpenMP directive"
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# barrier
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

sincroniza todos los subprocesos en un equipo; todos los subprocesos en pausa en la barrera, hasta que todos los subprocesos se ejecuten la barrera.  
  
## Sintaxis  
  
```  
#pragma omp barrier  
```  
  
## Comentarios  
 la directiva de `barrier` no admite ninguna cláusula de OpenMP.  
  
 Para obtener más información, vea [2.6.3 barrier Directive](../../../parallel/openmp/2-6-3-barrier-directive.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo utilizar `barrier`, vea [master](../../../parallel/openmp/reference/master.md).  
  
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)