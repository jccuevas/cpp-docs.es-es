---
title: "Clases de ventana de marco | Microsoft Docs"
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
  - "clases [C++], ventana"
  - "ventanas de marco de documento, clases"
  - "clases de ventana de marco"
  - "clases de ventana de marco, acerca de clases de ventana de marco"
  - "MDI [C++], ventanas de marco"
  - "MFC [C++], ventanas de marco"
  - "interfaz de único documento (SDI), ventanas de marco"
  - "clases de ventana, marco"
  - "ventanas [C++], MDI"
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de ventana de marco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada aplicación tiene una “ventana de marco principal”, una ventana de escritorio que normalmente tiene el nombre de la aplicación en su leyenda.  Cada documento tiene normalmente una “ventana de marco de documento”. Una ventana de marco de documento contiene al menos una vista, que muestra los datos del documento.  
  
## Cuadro Windows en aplicaciones SDI y MDI  
 Para una aplicación SDI, hay una ventana de marco derivada de la clase [CFrameWnd](../mfc/reference/cframewnd-class.md).  Esta ventana es la ventana de marco principal y la ventana de marco de documento.  Para una aplicación MDI, la ventana de marco principal se deriva de la clase [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), las ventanas de marco de documento, que son ventanas secundarias MDI, se derivan de la clase [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).  
  
## Utilice la clase de la Cuadro\- ventana, o Deriva de?  
 Estas clases proporcionan la mayor parte de la funcionalidad de la cuadro\- ventana que necesita para las aplicaciones.  En circunstancias normales, el comportamiento predeterminado y el aspecto que proporcionan se adaptarán las necesidades.  Si necesita funcionalidad adicional, derive de estas clases.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Clases de la Cuadro\-ventana creadas por el Asistente para aplicaciones](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Estilos de la Cuadro\-ventana](../mfc/frame-window-styles-cpp.md)  
  
-   [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## Vea también  
 [Ventanas de marco](../mfc/frame-windows.md)