---
title: "Ventanas de marco | Microsoft Docs"
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
  - "CFrameWnd (clase), ventanas de marco"
  - "ventanas de marco de documento"
  - "ventanas de marco [C++]"
  - "ventanas de marco [C++], acerca de las ventanas de marco"
  - "MDI [C++], ventanas de marco"
  - "MFC [C++], ventanas de marco"
  - "interfaz de único documento (SDI)"
  - "interfaz de único documento (SDI), ventanas de marco"
  - "ventanas divisoras, y ventanas de marco"
  - "vistas [C++], y ventanas de marco"
  - "clases de ventana [C++], marco"
  - "ventanas [C++], MDI"
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ventanas de marco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando una aplicación se ejecuta en Windows, el usuario interactúa con documentos mostrados en ventanas de marco.  Una ventana de marco de documento tiene dos componentes principales: el cuadro y el contenido que se cuadros.  Una ventana de marco de documento puede ser una ventana cuadro de [interfaz de un único documento](../mfc/sdi-and-mdi.md) \(SDI\) o una ventana secundaria de [interfaz de múltiples documentos](../mfc/sdi-and-mdi.md) \(MDI\).  Windows administra la mayor parte de la interacción del usuario con la ventana de marco: mover y cambiar el tamaño de la ventana, cerrarlo, y la minimizar y maximizarél de.  Administra el contenido dentro del cuadro.  
  
## Cuadro Windows y vistas  
 El marco de trabajo de MFC utiliza las ventanas de marco para contener las vistas.  Dos clases diferentes en MFC representan y administra los dos componentes — cuadro y el contenido \).  Una clase de la cuadro\- ventana administra el cuadro, y una clase de vista administra el contenido.  La ventana de vista es un elemento secundario de la ventana de marco.  Interacción de dibujo y otra de usuario con el documento tiene lugar en el área de cliente de la vista, no el área cliente de la ventana de marco.  La ventana de marco proporciona un cuadro visibles alrededor de una vista, completa con una barra de título y los controles de ventana estándar de como un menú, botones de control para minimizar y para maximizar la ventana, y controles para cambiar el tamaño de la ventana.  Los “contenido” constan del área de cliente de la ventana, que está ocupada totalmente en una ventana secundaria de la vista.  La ilustración siguiente muestra la relación entre una ventana de marco y una vista.  
  
 ![Vista de ventana de marco](../mfc/media/vc37fx1.png "vc37FX1")  
Vista y ventana de marco  
  
## Cuadro Windows y divisor Windows  
 Otra organización común es para la ventana de marco a diversas vistas en cuadro, normalmente mediante [ventana divisora](../mfc/multiple-document-types-views-and-frame-windows.md).  En una ventana divisora, el área de cliente de la ventana de marco es ocupa una ventana divisora, que a su vez tiene ventanas secundarias múltiples, denominada paneles, que son vistas.  
  
### ¿Sobre qué desea obtener más información?  
 **Temas generales de la ventana de marco**  
  
-   [Objetos de la ventana](../mfc/window-objects.md)  
  
-   [Clases de ventana frame](../mfc/frame-window-classes.md)  
  
-   [Las clases de la Cuadro\-ventana creadas por el Asistente para aplicaciones](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Estilos de ventana frame](../mfc/frame-window-styles-cpp.md)  
  
-   [Haga las ventanas de marco](../mfc/what-frame-windows-do.md)  
  
 **Temas del cuadro Windows de Utilizar**  
  
-   [Utilizando las ventanas de marco](../mfc/using-frame-windows.md)  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Ventanas de destrucción de cuadro](../mfc/destroying-frame-windows.md)  
  
-   [Administrar las ventanas secundarias MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Administrar la vista actual](../mfc/managing-the-current-view.md) en una ventana de marco que contiene más de una vista  
  
-   [Administrar menús, las barras de controles, y los aceleradores \(otros objetos que comparten el espacio de la ventana de marco\)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **Temas en características de la ventana de marco especial**  
  
-   Explorador o administrador de archivos de[Arrastrando y colocando los archivos](../mfc/dragging-and-dropping-files-in-a-frame-window.md) desde el archivo en una ventana de marco  
  
-   [Respuesta a \(DDE\) de intercambio de datos dinámicos](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [Estados de Semimodal: Ayuda de Windows contextual \(Orchestrating otras acciones de la ventana\)](../mfc/orchestrating-other-window-actions.md)  
  
-   [Estados de Semimodal: impresión y vista previa de impresión \(Orchestrating otras acciones de la ventana\)](../mfc/orchestrating-other-window-actions.md)  
  
 **Temas de Otros Tipos de Windows**  
  
-   [Con las vistas](../mfc/using-views.md)  
  
-   [Cuadros de diálogo](../mfc/dialog-boxes.md)  
  
-   [Controles](../mfc/controls-mfc.md)  
  
## Vea también  
 [Windows](../mfc/windows.md)