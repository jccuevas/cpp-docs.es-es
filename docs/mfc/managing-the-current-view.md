---
title: "Administrar la vista actual | Microsoft Docs"
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
helpviewer_keywords: 
  - "vista actual en una ventana de marco"
  - "desactivar vistas"
  - "ventanas de marco, vista actual"
  - "OnActivateView (método)"
  - "vistas, activar"
  - "vistas, y OnActivateView (método)"
  - "vistas, actuales"
  - "vistas, desactivar"
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Administrar la vista actual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como parte de la implementación predeterminada de las ventanas de marco, una ventana de marco realiza un seguimiento de la vista activa de a actualmente.  Si la ventana de marco contiene más de una vista, como por ejemplo en una ventana divisora, la vista actual es la vista más reciente en uso.  La vista activa es independiente de la ventana activa de Windows o el foco actual.  
  
 Cuando la vista activa, el marco notifica la vista actual llamando a la función miembro de [OnActivateView](../Topic/CView::OnActivateView.md) .  Puede indicar si la vista se está activada o desactivada examina el parámetro de `OnActivateView``bActivate` .  De forma predeterminada, `OnActivateView` establece el foco en la vista actual en la activación.  Puede reemplazar `OnActivateView` para realizar cualquier procesamiento especial cuando se desactiva o se reactivará la vista.  Por ejemplo, puede que desee proporcionar indicaciones visuales especiales para distinguir la vista activa de otra, vistas inactivas.  
  
 Una ventana de marco transmite a comandos su vista actual \(de activo\), como se describe en [Enrutamiento de comandos](../mfc/command-routing.md), como parte de enrutamiento estándar del comando.  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)