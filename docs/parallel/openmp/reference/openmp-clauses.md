---
title: "OpenMP Clauses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OpenMP Clauses
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

proporciona vínculos a las cláusulas utilizadas en el OpenMP API.  
  
 Visual C\+\+ admite las siguientes cláusulas de OpenMP:  
  
|Cláusula|Descripción|  
|--------------|-----------------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|Permite que los subprocesos tienen acceso al valor del subproceso principal, para una variable de [threadprivate](../../../parallel/openmp/reference/threadprivate.md) .|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|especifica que una o más variables se deben compartir entre todos los subprocesos.|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|especifica el comportamiento de variables unscoped en una región paralela.|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Especifica que cada subproceso debe tener una instancia de una variable, y que la variable se debe inicializar con el valor de la variable, porque existe antes de la construcción paralela.|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|Especifica si un bucle se debe ejecutar en paralelo o en serie.|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Especifica que la versión de contexto que agrega de la variable es igual a la versión privada de cualquier subproceso ejecuta la iteración final \(construcción de bucle for\) o la última sección \(secciones \#pragma\).|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|invalida la barrera implícita en una directiva.|  
|[num\_threads](../../../parallel/openmp/reference/num-threads.md)|Establece el número de subprocesos en un equipo de subproceso.|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Necesario en una instrucción paralela de [for](../../../parallel/openmp/reference/for-openmp.md) si se va una directiva de [ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md) a usar en el bucle.|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|Especifica que cada subproceso debe tener una instancia de una variable.|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|Especifica que una o más variables que son privadas para cada subproceso son el asunto de una operación de reducción en el final de la región paralela.|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|Se aplica a la directiva de [for](../../../parallel/openmp/reference/for-openmp.md) .|  
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|especifica que una o más variables se deben compartir entre todos los subprocesos.|  
  
## Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)