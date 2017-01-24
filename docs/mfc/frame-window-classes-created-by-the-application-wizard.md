---
title: "Clases de ventana de marco creadas por el Asistente para aplicaciones | Microsoft Docs"
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
  - "CMainFrame"
  - "CMainFrame::PreCreateWindow"
  - "CMainFrame.PreCreateWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para aplicaciones [C++], clases de ventana de marco creadas por"
  - "CFrameWnd (clase), ventanas de marco"
  - "clases [C++], ventana de marco"
  - "CMainFrame (clase)"
  - "CMDIChildWnd (clase), ventanas de marco"
  - "CMDIFrameWnd (clase), ventanas de marco"
  - "clases de ventana de marco, creadas mediante asistentes para aplicaciones"
  - "clases de ventana"
  - "clases de ventana, marco"
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de ventana de marco creadas por el Asistente para aplicaciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza [Asistente para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md) para crear una aplicación esqueleto, además de la aplicación, documentos, y clases de vista, el Asistente para aplicaciones crea una clase derivada de la cuadro\- ventana para la ventana de marco principal de la aplicación.  La clase se denomina `CMainFrame` de manera predeterminada, los archivos que lo contienen se denominan MAINFRM.H y MAINFRM.CPP.  
  
 Si la aplicación es SDI, la clase de `CMainFrame` se deriva de la clase [CFrameWnd](../mfc/reference/cframewnd-class.md).  
  
 Si la aplicación es MDI, `CMainFrame` se deriva de la clase [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md).  En este caso `CMainFrame` implementa el cuadro principal, que contiene el menú, la barra de herramientas, y barras de estado.  El Asistente para aplicaciones no derivar una clase de la cuadro\- ventana en el nuevo documento automáticamente.  En su lugar, utiliza la implementación predeterminada en [Clase de CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).  El marco de trabajo de MFC crea una ventana secundaria para contener cada vista \(que puede ser de `CScrollView`escrito, `CEditView`, `CTreeView`, `CListView`, etc.\) que la aplicación requiere.  Si necesita personalizar la ventana de marco de documento, puede crear una clase de la cuadro\- ventana en el nuevo documento \(vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md)\).  
  
 Si decide admitir una barra de herramientas, la clase también tiene variables miembro de [CToolBar](../mfc/reference/ctoolbar-class.md) escrito y de [CStatusBar](../mfc/reference/cstatusbar-class.md) y una función de controlador de mensajes `OnCreate` para inicializar dos [barras de controles](../mfc/control-bars.md).  
  
 Estas clases cuadro\- ventana funcionan como se creado, pero ampliar su funcionalidad, debe agregar a variables miembro y el miembro funciona.  Puede que también desee hacer que las clases de ventana administran otros mensajes de Windows.  Para obtener más información, vea [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## Vea también  
 [Clases de ventana de marco](../mfc/frame-window-classes.md)   
 [Archivos de encabezado y código fuente de controles o programas MFC](../ide/mfc-program-or-control-source-and-header-files.md)