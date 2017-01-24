---
title: "firstprivate | Microsoft Docs"
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
  - "firstprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "firstprivate OpenMP clause"
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# firstprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que cada subproceso debe tener una instancia de una variable, y que la variable se debe inicializar con el valor de la variable, porque existe antes de la construcción paralela.  
  
## Sintaxis  
  
```  
firstprivate(var)  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`var`|La variable para tener instancias en cada subproceso y que se inicializa con el valor de la variable, porque existe antes de la construcción paralela.  Si se especifica más de una variable, los nombres de variable separados por una coma.|  
  
## Comentarios  
  
## Comentarios  
 `firstprivate` se aplica a las siguientes directivas:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 Para obtener más información, vea [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).  
  
## Ejemplo  
 Para obtener un ejemplo de `firstprivate`utilizando, vea el ejemplo de [private](../../../parallel/openmp/reference/private-openmp.md).  
  
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)