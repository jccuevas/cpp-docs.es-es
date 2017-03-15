---
title: "Windows | Microsoft Docs"
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
  - "MFC [C++], ventanas"
  - "objetos [C++], ventana"
  - "Window (objetos) [C++], Framework MFC"
  - "ventanas [C++]"
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta familia de casos cubre los objetos de la ventana en el marco de trabajo de MFC.  Todas las ventanas de MFC se derivan de la clase [CWnd](../mfc/reference/cwnd-class.md), incluidas las ventanas de marco, las vistas, los cuadros de diálogo, y controles.  
  
 El primer grupo de casos describe [objetos de la ventana](../mfc/window-objects.md) en general.  Haga referencia a este grupo para obtener información general sobre los objetos de la ventana de C\+\+, cómo encapsulan un HWND, y cómo usarlo para crear dispone de las ventanas, como ventanas secundarias.  
  
 El segundo grupo de casos describe [ventanas de marco](../mfc/frame-windows.md)— ventanas que abre un cuadro alrededor de contenido — en particular.  Haga referencia a este grupo para obtener información sobre cómo el marco de trabajo de MFC administra las ventanas de marco y el contenido que ellos cuadro, incluidas las barras de controles y vistas.  
  
## ¿Sobre qué desea obtener más información?  
 *Temas de objetos de la ventana en General*  
  
-   [Objetos de la ventana](../mfc/window-objects.md)  
  
-   [Relación entre los objetos de la ventana de c\+\+. e identificadores de HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Clases de ventana derivadas](../mfc/derived-window-classes.md)  
  
-   [Crear objetos de la ventana](../mfc/creating-windows.md)  
  
-   [Objetos de destrucción de la ventana](../mfc/destroying-window-objects.md)  
  
-   [Registrar la ventana “clase”](../mfc/registering-window-classes.md)  
  
-   [Trabajar con objetos de la ventana](../mfc/working-with-window-objects.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md): objetos que facilitan la creación de Windows independiente del dispositivo  
  
-   [Objetos gráficos](../mfc/graphic-objects.md): lápices, pinceles, fuentes, mapas de bits, paletas, regiones  
  
 *Los temas de ventana de marco*  
  
-   [Ventanas frame](../mfc/frame-windows.md): objetos de la ventana que proporcionan los cuadros  
  
-   [Ventanas y vistas frame](../mfc/frame-windows.md)  
  
-   [Clases de la Cuadro\-ventana](../mfc/frame-window-classes.md)  
  
-   [Estilos de la Cuadro\-ventana](../mfc/frame-window-styles-cpp.md)  
  
-   [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Haga las ventanas de marco](../mfc/what-frame-windows-do.md)  
  
-   [Utilizando las ventanas de marco](../mfc/using-frame-windows.md)  
  
-   [Administrar las ventanas de MD\/Child \(la ventana de MDICLIENT\)](../mfc/managing-mdi-child-windows.md)  
  
-   [Administrar menús, las barras de controles, y los aceleradores](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [CFrameWnd](../mfc/reference/cframewnd-class.md)  
  
-   [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
  
-   [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
  
-   [Con las vistas](../mfc/using-views.md)  
  
-   [Tipos de documento, vistas, y chapter varias Windows \(ventanas divisoras\)](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Mensajes \(mapas y funciones controladoras\)](../mfc/messages.md)  
  
 *Cree y Destroy Windows*  
  
-   [Flujo general de creación de la ventana](../mfc/general-window-creation-sequence.md)  
  
-   [Destruir los objetos de la ventana](../mfc/destroying-window-objects.md)  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Destruya las ventanas de marco](../mfc/destroying-frame-windows.md)  
  
 *Crear ventanas divisoras*  
  
-   [Cree las ventanas divisoras](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
 *Administrar las ventanas secundarias y la vista actual*  
  
-   [Administrar las ventanas secundarias MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Administrar la vista actual](../mfc/managing-the-current-view.md)  
  
-   [Administrar los menús, las barras de controles, y los aceleradores](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 *Trabajo con contextos y estilos de ventana de dispositivo*  
  
-   [Utilice los lápices y otros objetos gráficos en un contexto de dispositivo](../mfc/graphic-objects.md)  
  
-   [Cambie los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Barras de herramientas](../mfc/toolbars.md)   
 [Barras de estado](../mfc/status-bars.md)   
 [Barras de cuadro de diálogo](../mfc/dialog-bars.md)