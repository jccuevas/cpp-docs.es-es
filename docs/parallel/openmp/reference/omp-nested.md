---
title: "OMP_NESTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_NESTED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_NESTED OpenMP environment variable"
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# OMP_NESTED
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica si el paralelismo anidados está habilitado, a menos que el paralelismo anidados está habilitado o deshabilitado con `omp_set_nested`.  
  
## Sintaxis  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## Comentarios  
 La variable de entorno `OMP_NESTED` puede reemplazarse por la función de [omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md) .  
  
 El valor predeterminado de implementación de Visual C\+\+ del estándar de OpenMP se `OMP_DYNAMIC=FALSE`.  
  
 Para obtener más información, vea [4.4 OMP\_NESTED](../Topic/4.4%20OMP_NESTED.md).  
  
## Ejemplo  
 El comando siguiente establece la variable de entorno `OMP_NESTED` TRUE:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 El comando siguiente muestra la configuración actual de la variable de entorno `OMP_NESTED` :  
  
```  
set OMP_NESTED  
```  
  
## Vea también  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)