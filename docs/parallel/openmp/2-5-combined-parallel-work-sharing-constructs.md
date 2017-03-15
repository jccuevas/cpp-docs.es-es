---
title: "2.5 Combined Parallel Work-sharing Constructs | Microsoft Docs"
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
ms.assetid: 45936e5a-c62a-4eea-a8f4-232210c9d0c8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.5 Combined Parallel Work-sharing Constructs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las construcciones paralelas combinadas de la división de trabajo son accesos directos para especificar una región paralela que sólo contiene una construcción de división del trabajo.  La semántica de estas directivas es idéntica a la de especificar explícitamente una directiva de **Paralelo** seguida de una única construcción de división del trabajo.  
  
 Las secciones siguientes describen las construcciones paralelas combinadas de la división del trabajo:  
  
-   la directiva de **paralelo para** .  
  
-   la directiva de **secciones paralelas** .