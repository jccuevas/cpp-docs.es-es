---
title: "OMP_SCHEDULE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_SCHEDULE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_SCHEDULE OpenMP environment variable"
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# OMP_SCHEDULE
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

modifica el comportamiento de la cláusula de [schedule](../../../parallel/openmp/reference/schedule.md) cuando `schedule(runtime)` se especifica en una directiva de `for` o de `parallel for` .  
  
## Sintaxis  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## Comentarios  
 donde  
  
 `size` \(opcional\)  
 Especifica el tamaño de iteraciones.  `size` debe ser un entero positivo.  El valor predeterminado es 1, excepto cuando `type` es estático.  no válido cuando `type` es `runtime`.  
  
 `type`  
 la clase de programación:  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## Comentarios  
 El valor predeterminado de implementación de Visual C\+\+ del estándar de OpenMP se `OMP_SCHEDULE=static,0`.  
  
 Para obtener más información, vea [4.1 OMP\_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).  
  
## Ejemplo  
 El comando siguiente establece la variable de entorno **OMP\_SCHEDULE** :  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 El comando siguiente muestra la configuración actual de la variable de entorno **OMP\_SCHEDULE** :  
  
```  
set OMP_SCHEDULE  
```  
  
## Vea también  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)