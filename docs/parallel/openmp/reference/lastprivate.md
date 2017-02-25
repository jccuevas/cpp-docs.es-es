---
title: "lastprivate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "lastprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lastprivate OpenMP clause"
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# lastprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que la versión de contexto que agrega de la variable es igual a la versión privada de cualquier subproceso ejecuta la iteración final \(construcción de bucle for\) o la última sección \(secciones \#pragma\).  
  
## Sintaxis  
  
```  
lastprivate(var)  
```  
  
## Comentarios  
 donde  
  
 `var`  
 La variable de la que está el igual a la versión privada cualquier subproceso ejecuta la iteración final \(construcción de bucle for\) o la última sección \(secciones \#pragma\).  
  
## Comentarios  
 `lastprivate` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, vea [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## Ejemplo  
 Vea [schedule](../../../parallel/openmp/reference/schedule.md) para obtener un ejemplo de la cláusula de `lastprivate` mediante.  
  
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)