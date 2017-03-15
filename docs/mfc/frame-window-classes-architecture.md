---
title: "Clases de ventana de marco (Arquitectura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "clases de ventana de marco, arquitectura documento/vista"
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de ventana de marco (Arquitectura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En arquitectura documento\/vista, las ventanas de marco son ventanas que contienen una ventana de vista.  También admiten tener barras de control asociadas a ellos.  
  
 En las aplicaciones de \(MDI\) de interfaz de múltiples documentos, la ventana principal se deriva de `CMDIFrameWnd`.  Contiene indirectamente cuadros de documentos, que son objetos de `CMDIChildWnd` .  Los objetos de `CMDIChildWnd` , a su vez, contienen las vistas de los documentos.  
  
 En las aplicaciones de \(SDI\) de interfaz de un único documento, la ventana principal, derivada de `CFrameWnd`, contiene la vista del documento actual.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación SDI.  También la clase base para todas las clases de ventana de marco.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 La clase base para la ventana de marco principal de una aplicación MDI.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 La clase base para las ventanas de marco de documento de una aplicación MDI.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Proporciona la ventana cuadro de una vista a un documento de servidor se edita en contexto.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)