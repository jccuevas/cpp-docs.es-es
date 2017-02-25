---
title: "Clases de arquitectura de aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de arquitectura de aplicaciones"
  - "clases [C++], MFC"
  - "MFC [C++], desarrollo de aplicaciones"
  - "MFC [C++], clases"
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de arquitectura de aplicaciones MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases de esta categoría contribuyen a la arquitectura de una aplicación de .NET framework.  Proporcionan la funcionalidad común a la mayoría de las aplicaciones.  Complete el marco para agregar funcionalidad específica de la aplicación.  Normalmente, para ello derivar clases nuevas de las clases de la arquitectura, y agregando nuevos miembros o reemplazando el miembro existente funciona.  
  
 [Asistentes para aplicaciones](../mfc/reference/mfc-application-wizard.md) genera varios tipos de aplicaciones, que utilizan el marco de aplicación de maneras de son iguales.  Las aplicaciones SDI \(interfaz de un único documento\) y MDI \(interfaz de múltiples documentos\) hacen uso completo de una parte del marco denominado arquitectura documento\/vista.  Otros tipos de aplicaciones, como aplicaciones diálogo\- basadas en, formulario\- función aplicaciones, y los archivos DLL, utilice sólo algunas de las características de la arquitectura documento\/vista.  
  
 Las aplicaciones de documentos y vistas contienen uno o más conjuntos de documentos, de vistas, y ventanas de marco.  Un objeto de plantilla de documento asociado clases para cada conjunto de documento y vista\/cuadro.  
  
 Aunque no tenga que utilizar la arquitectura documento\/vista en la aplicación MFC, hay varias ventajas para ello.  Compatibilidad OLE de contenedor y servidor de MFC se basa en la arquitectura documento\/vista, al igual que admiten para imprimir y vista previa de impresión.  
  
 Todas las aplicaciones MFC tienen al menos dos objetos: un objeto application derivado de [CWinApp](../mfc/reference/cwinapp-class.md), y algún tipo de objeto de la ventana principal, derivada \(a menudo indirectamente\) de [CWnd](../mfc/reference/cwnd-class.md). \(Más a menudo, la ventana principal se deriva de [CFrameWnd](../mfc/reference/cframewnd-class.md), de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), o de [CDialog](../mfc/reference/cdialog-class.md), que se derivan de `CWnd`.\)  
  
 Las aplicaciones que utilizan la arquitectura documento\/vista contienen objetos adicionales.  Los objetos principales son:  
  
-   Un objeto application derivado de la clase [CWinApp](../mfc/reference/cwinapp-class.md), como se mencionó anteriormente.  
  
-   Uno o más objetos de la clase document derivados de la clase [CDocument](../mfc/reference/cdocument-class.md).  Los objetos de la clase document son responsables de la representación interna de datos manipulando en la vista.  Pueden estar asociados a un archivo de datos.  
  
-   Uno o más objetos de vista derivados de la clase [CView](../mfc/reference/cview-class.md).  Cada vista es una ventana que está asociado a un documento y se asocia a una ventana de marco.  Las vistas muestran y manipulan los datos contenidos en un objeto de clase de documento.  
  
 Las aplicaciones de documentos y vistas contienen las ventanas de marco \(derivadas de [CFrameWnd](../mfc/reference/cframewnd-class.md)\) y las plantillas de documento \(derivadas de [CDocTemplate](../mfc/reference/cdoctemplate-class.md)\).  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)