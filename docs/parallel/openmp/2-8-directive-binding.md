---
title: "2.8 Directive Binding | Microsoft Docs"
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
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.8 Directive Binding
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El enlace dinámico de directivas debe observar las reglas siguientes:  
  
-   **Para**, **secciones**, **solo**, **principal**, y las directivas de **barrera** enlazados a **Paralelo**dinámicamente que agrega, si existe, independientemente del valor de cualquier cláusula de **If \[SQL2008\]** que puede estar presente en esa directiva.  Si no se está ejecutando ninguna región paralela actualmente, las directivas se ejecutan en un equipo compuesto por sólo el subproceso principal.  
  
-   La directiva de **consultar** enlaza el párrafo dinámicamente envolvente.  
  
-   La directiva de **atómico** aplica el acceso exclusivo con respecto a las directivas de **atómico** en todos los subprocesos, no solo el equipo actual.  
  
-   La directiva de **Crtico** aplica el acceso exclusivo con respecto a las directivas de **Crtico** en todos los subprocesos, no solo el equipo actual.  
  
-   Una directiva nunca puede enlazarse a cualquier directiva fuera de **Paralelo**dinámicamente que agrega más próximo.