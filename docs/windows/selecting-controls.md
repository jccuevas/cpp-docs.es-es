---
title: "Selecting Controls | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Dialog editor, selecting controls"
  - "dominant controls"
  - "dialog box controls, selecting in editor"
  - "controls [C++], selecting"
  - "size, controls"
  - "controls [C++], dominant"
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Selecting Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles se seleccionan para poder cambiar su tamaño, alinearlos, moverlos, copiarlos o eliminarlos, y después realizar la operación que se desee.  En la mayoría de los casos, deberán seleccionarse varios controles para utilizar las herramientas de cambio de tamaño y alineación en la [barra de herramientas del Editor de cuadros de diálogo](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
 Cuando un control está seleccionado, aparece rodeado por un borde sombreado con cuadros de tamaño \(pequeños cuadros que aparecen en el borde de selección\) sólidos \(activos\) o huecos \(inactivos\).  Si están seleccionados varios controles, el control dominante tendrá cuadros de tamaño sólidos, mientras que los demás tendrán cuadros vacíos.  
  
 Cuando se cambia el tamaño o la alineación de varios controles a la vez, el Editor de cuadros de diálogo usa el "control dominante" para determinar el tamaño y la alineación de los demás controles.  De forma predeterminada, el control dominante es el primero que se selecciona.  
  
-   [Seleccionar varios controles](../mfc/selecting-multiple-controls.md)  
  
-   [Especificar el control dominante](../mfc/specifying-the-dominant-control.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)