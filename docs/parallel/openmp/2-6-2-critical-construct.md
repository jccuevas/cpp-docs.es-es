---
title: "2.6.2 critical Construct | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.2 critical Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de **Crtico** identifica una construcción que limite la ejecución del bloque estructurado asociado a un único subproceso cada vez.  La sintaxis de la directiva de **Crtico** es la siguiente:  
  
```  
#pragma omp critical [(name)]  new-line  
   structured-block  
```  
  
 *Un nombre* opcional puede utilizarse para identificar la región crítica.  Los identificadores utilizados para identificar una región crítica poseen vinculación externa y están en un espacio de nombres que es independiente de los espacios de nombres utilizados por etiquetas, etiquetas, miembros, y los identificadores normales.  
  
 Un subproceso espera al principio de una región crítica hasta que otro subproceso ejecuta una región crítica \(en cualquier parte del programa\) con el mismo nombre.  Todo el mapa sin nombre de las directivas de **Crtico** en el mismo nombre sin especificar.