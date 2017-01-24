---
title: "shared (OpenMP) | Microsoft Docs"
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
  - "Shared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shared OpenMP clause"
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# shared (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

especifica que una o más variables se deben compartir entre todos los subprocesos.  
  
## Sintaxis  
  
```  
shared(var)  
```  
  
## Comentarios  
 donde  
  
 `var`  
 Uno más variables a compartir.  Si se especifica más de una variable, los nombres de variable separados por una coma.  
  
## Comentarios  
 Otra manera de compartir variables entre subprocesos es mediante la cláusula de [copyprivate](../../../parallel/openmp/reference/copyprivate.md) .  
  
 `shared` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, vea [2.7.2.4 shared](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## Ejemplo  
 Vea [private](../../../parallel/openmp/reference/private-openmp.md) para obtener un ejemplo de `shared`mediante.  
  
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)