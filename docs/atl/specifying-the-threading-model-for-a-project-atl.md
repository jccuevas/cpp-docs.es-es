---
title: "Especificar el modelo de subprocesos de un proyecto (ATL) | Microsoft Docs"
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
helpviewer_keywords: 
  - "_ATL_APARTMENT_THREADED (macro)"
  - "_ATL_FREE_THREADED (macro)"
  - "_ATL_SINGLE_THREADED (macro)"
  - "ATL, multithreading"
  - "subprocesamiento [ATL], modelos"
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Especificar el modelo de subprocesos de un proyecto (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las macros siguientes están disponibles especificar el modelo de subprocesos de un proyecto ATL:  
  
|Macro|Instrucciones para utilizar|  
|-----------|---------------------------------|  
|\_ATL\_SINGLE\_THREADED|Defina si todos los objetos utilizan el modelo de subproceso único.|  
|\_ATL\_APARTMENT\_THREADED|defina si uno o más de los objetos utilizan subproceso controlado.|  
|\_ATL\_FREE\_THREADED|Defina si uno o más de los objetos libre o el subprocesamiento neutro.  el código existente puede contener referencias a [\_ATL\_MULTI\_THREADED](../Topic/_ATL_MULTI_THREADED.md)macro equivalente.|  
  
 Si no define ninguna de estas macros para el proyecto, el \_ATL\_FREE\_THREADED entrará en vigor.  
  
 Las macros afectan al rendimiento en tiempo de ejecución como sigue:  
  
-   Especificar la macro que corresponde a los objetos del proyecto puede mejorar el rendimiento en tiempo de ejecución.  
  
-   Especificar un alto nivel de la macro, por ejemplo si especifica el \_ATL\_APARTMENT\_THREADED cuando todos los objetos de tipo haber con, degradará ligeramente rendimiento en tiempo de ejecución.  
  
-   Especificar un nivel inferior de la macro, por ejemplo, si especifica el \_ATL\_SINGLE\_THREADED cuando uno o más de los objetos utilizan subproceso controlado o subprocesamiento libre, puede producir un error en la aplicación en tiempo de ejecución.  
  
 Vea [Opciones, asistente para objetos simples ATL](../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)