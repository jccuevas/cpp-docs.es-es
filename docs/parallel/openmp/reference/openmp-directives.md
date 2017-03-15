---
title: "OpenMP Directives | Microsoft Docs"
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
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OpenMP Directives
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

proporciona vínculos a las directivas utilizadas en el OpenMP API.  
  
 Visual C\+\+ admite las siguientes directivas de OpenMP:  
  
|Directiva|Descripción|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|Especifica que una ubicación de memoria que se actualizará atómico.|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|sincroniza todos los subprocesos en un equipo; todos los subprocesos en pausa en la barrera, hasta que todos los subprocesos se ejecuten la barrera.|  
|[critical](../../../parallel/openmp/reference/critical.md)|Especifica que el código se ejecuta sólo en un subproceso cada vez.|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|Hace que el trabajo realizado en un bucle for dentro de una región paralela que se va a dividir entre los subprocesos.|  
|[master](../../../parallel/openmp/reference/master.md)|Especifica que sólo el threadshould principal ejecuta una sección del programa.|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Especifica que el código en paralelo del bucle se debe ejecutar como un bucle secuencial.|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|Define una región paralela, que es el código que se ejecutará por varios subprocesos en paralelo.|  
|[sections](../../../parallel/openmp/reference/sections-openmp.md)|identifica las secciones de código que se dividirán entre todos los subprocesos.|  
|[single](../../../parallel/openmp/reference/single.md)|Permite especificar que una sección de código debe ejecutarse en un subproceso, no necesariamente el subproceso principal.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Especifica que una variable es privada para un subproceso.|  
  
## Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)