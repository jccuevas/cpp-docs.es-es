---
title: "OMP_DYNAMIC | Microsoft Docs"
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
  - "OMP_DYNAMIC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_DYNAMIC OpenMP environment variable"
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OMP_DYNAMIC
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica si el runtime de OpenMP puede ajustar el número de subprocesos en una región paralela.  
  
## Sintaxis  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## Comentarios  
 La variable de entorno `OMP_DYNAMIC` puede reemplazarse por la función de [omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) .  
  
 El valor predeterminado de implementación de Visual C\+\+ del estándar de OpenMP se `OMP_DYNAMIC=FALSE`.  
  
 Para obtener más información, vea [4.3 OMP\_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).  
  
## Ejemplo  
 El comando siguiente establece la variable de entorno `OMP_DYNAMIC` TRUE:  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 El comando siguiente muestra la configuración actual de la variable de entorno `OMP_DYNAMIC` :  
  
```  
set OMP_DYNAMIC  
```  
  
## Vea también  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)