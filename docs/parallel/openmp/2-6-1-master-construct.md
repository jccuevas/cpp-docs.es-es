---
title: "2.6.1 master Construct | Microsoft Docs"
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
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.1 master Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de **principal** identifica una construcción que especifique un bloque estructurado que ejecute el subproceso principal del equipo.  La sintaxis de la directiva de **principal** es la siguiente:  
  
```  
#pragma omp master new-line  
   structured-block  
```  
  
 Otros subprocesos del equipo no ejecutan el bloque estructurado asociado.  No hay barrera implícitamente en la entrada a o sale de la construcción principal.