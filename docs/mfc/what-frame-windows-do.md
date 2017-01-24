---
title: "&#191;Para qu&#233; sirven las ventanas de marco? | Microsoft Docs"
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
  - "ventanas de marco, acerca de las ventanas de marco"
  - "ventanas de marco, tareas"
  - "MFC, ventanas de marco"
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Para qu&#233; sirven las ventanas de marco?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Además de simplemente enmarcar una vista, las ventanas de marco son responsables de las tareas numerosas implicadas en la coordinación de cuadro con la vista y con la aplicación.  [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) heredar de [CFrameWnd](../mfc/reference/cframewnd-class.md), junto con las funciones de `CFrameWnd` así como nuevas capacidades envolventes.  Los ejemplos de las ventanas secundarias ven, controles como botones y cuadros de lista, y las barras de controles, incluidas las barras de herramientas, barras de estado, y las barras de cuadro de diálogo.  
  
 La ventana de marco es responsable de administrar el diseño de sus ventanas secundarias.  En el marco de trabajo de MFC, posiciones de la ventana de un cuadro cualquier barras de controles, vistas, y otras ventanas secundarias dentro del área cliente.  
  
 La ventana de marco también transmite a comandos sus vistas y puede responder a los mensajes de notificación de las ventanas de control.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Barras de control \(cómo cupieron en la ventana de marco\)](../mfc/control-bars.md)  
  
-   [Administrar menús, las barras de controles, y los aceleradores \(cómo cupieron en la ventana de marco\)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [Enrutamiento de comandos \(de la ventana de marco a la vista y otros destinos de comando\)](../mfc/command-routing.md)  
  
-   [Arquitectura de \/View del documento](../mfc/document-view-architecture.md)  
  
-   [Barras de controles](../mfc/control-bars.md)  
  
-   [Controles](../mfc/controls-mfc.md)  
  
## Vea también  
 [Ventanas de marco](../mfc/frame-windows.md)