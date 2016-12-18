---
title: "2.9 Directive Nesting | Microsoft Docs"
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
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.9 Directive Nesting
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El anidamiento dinámico de directivas debe observar las reglas siguientes:  
  
-   Una directiva de **Paralelo** dentro de otro **Paralelo** establece dinámicamente lógicamente un nuevo equipo, que consta sólo del subproceso actual, a menos que se habilite el paralelismo anidados.  
  
-   **Para**, **secciones**, y las directivas de **solo** que enlazan al mismo **Paralelo** no pueden estar anidados dentro de otros.  
  
-   Las directivas de**Crtico** con el mismo nombre no pueden anidarse dentro de otros.  Observe que esta restricción no es suficiente para evitar el interbloqueo.  
  
-   **Para**, **secciones**, y las directivas de **solo** no se permiten en la extensión dinámica de **Crtico**, de **consultar**, y de las regiones de **principal** si las directivas se enlazan a mismo **Paralelo** que regiones.  
  
-   las directivas de**barrera** no se permiten en la extensión dinámica de **Para**, de **consultar**, de **secciones**, de **solo**, de **principal**, y de las regiones de **Crtico** si las directivas se enlazan a mismo **Paralelo** que regiones.  
  
-   las directivas de**principal** no se permiten en la extensión dinámica de **Para**, de **secciones**, y las directivas de **solo** si las directivas de **principal** enlazan al mismo **Paralelo** que las directivas de división del trabajo.  
  
-   las directivas de**consultar** no se permiten en la extensión dinámica de las regiones de **Crtico** si las directivas se enlazan a mismo **Paralelo** que regiones.  
  
-   Cualquier directiva permitido cuando ejecuta dinámicamente dentro de una región paralela también se permite cuando se ejecuta fuera de una región paralela.  Cuando se ejecuta dinámicamente fuera de una región paralela definida por el usuario, la directiva es ejecutada por un equipo compuesto por sólo el subproceso principal.