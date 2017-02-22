---
title: "default (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default OpenMP clause"
  - "defaults, OpenMP clause"
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# default (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

especifica el comportamiento de variables unscoped en una región paralela.  
  
## Sintaxis  
  
```  
default(shared | none)  
```  
  
## Comentarios  
 `shared`, que es en efecto si la cláusula de `default` no se especifica, significa que cualquier variable en una región paralela se tratará como si se hubiera especificado con la cláusula de [shared](../../../parallel/openmp/reference/shared-openmp.md) .  `none` significa que cualquier variable usada en una región paralela que no estén con [private](../../../parallel/openmp/reference/private-openmp.md), [shared](../../../parallel/openmp/reference/shared-openmp.md), [reduction](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), o la cláusula de [lastprivate](../../../parallel/openmp/reference/lastprivate.md) provocará un error del compilador.  
  
 `default` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, vea [2.7.2.5 default](../../../parallel/openmp/2-7-2-5-default.md).  
  
## Ejemplo  
 Vea [private](../../../parallel/openmp/reference/private-openmp.md) para obtener un ejemplo de `default`mediante.  
  
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)