---
title: "2.4 Work-sharing Constructs | Microsoft Docs"
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
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4 Work-sharing Constructs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una construcción de división de trabajo enruta la ejecución de la instrucción asociada entre los miembros del equipo que les.  Las directivas de división del trabajo no inician nuevos subprocesos, y no hay barrera implícitamente en la entrada a una construcción de división del trabajo.  
  
 La secuencia de construcciones de división del trabajo y de directivas de **barrera** encontradas debe ser el mismo para cada subproceso de un equipo.  
  
 OpenMP define las siguientes construcciones de división del trabajo, que se describen en las secciones siguientes:  
  
-   directiva de**Para**  
  
-   directiva de**secciones**  
  
-   directiva de**solo**