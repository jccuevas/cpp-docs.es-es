---
title: "Setting the Width of a Horizontal Scroll Bar | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "list controls, scroll bar width"
  - "CListBox::SetHorizontalExtent"
  - "controls [C++], scroll bar"
  - "scroll bars, displaying in controls"
  - "horizontal scroll bar width"
  - "CListBox class, scroll bar width"
  - "scroll bars, width"
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Setting the Width of a Horizontal Scroll Bar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se agrega un cuadro de lista con una barra de desplazamiento horizontal a un cuadro de diálogo por medio de clases MFC, la barra de desplazamiento no aparecerá automáticamente en la aplicación.  
  
### Para que aparezca la barra de desplazamiento  
  
1.  Defina un ancho máximo para el elemento más ancho llamando a [CListBox::SetHorizontalExtent](../Topic/CListBox::SetHorizontalExtent.md) en el código.  
  
     Si no se establece este valor, la barra de desplazamiento no aparecerá, aunque los elementos del cuadro de lista sean más anchos que el cuadro.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 MFC  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)