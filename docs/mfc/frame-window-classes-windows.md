---
title: "Clases de ventana de marco (Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.frame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de ventana de marco, referencia"
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de ventana de marco (Windows)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las ventanas de marco son ventanas que cuadro una aplicación o parte de una aplicación.  Las ventanas de capítulos normalmente contienen otras ventanas, como vistas, barras de herramientas, y barras de estado.  En el caso de `CMDIFrameWnd`, pueden contener objetos de `CMDIChildWnd` indirectamente.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación SDI.  También la clase base para todas las clases de ventana de marco.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación MDI.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 La clase base para las ventanas de marco de documento de una aplicación MDI.  
  
 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)  
 Una ventana de media altura de cuadro consultada normalmente alrededor de las barras de herramientas flotante.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Proporciona la ventana cuadro de una vista a un documento de servidor se edita en contexto.  
  
## Clase relacionada  
 La clase `CMenu` proporciona una interfaz a través de la que obtener acceso al menú de la aplicación.  Es útil para manipular menús dinámicamente en tiempo de ejecución; por ejemplo, al agregar o eliminar elementos de menú según el contexto.  Aunque los menús son los más a menudo con las ventanas de marco, también se pueden utilizar con los cuadros de diálogo y otras ventanas de nonchild.  
  
 [CMenu](../mfc/reference/cmenu-class.md)  
 Encapsula un identificador de `HMENU` a la barra de menús y los menús emergentes de la aplicación.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)