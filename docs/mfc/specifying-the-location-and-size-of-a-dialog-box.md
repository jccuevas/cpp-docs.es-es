---
title: "Specifying the Location and Size of a Dialog Box | Microsoft Docs"
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
  - "dialog boxes, size"
  - "dialog boxes, positioning"
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Specifying the Location and Size of a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ubicación y el tamaño de un cuadro de diálogo, así como la ubicación y el tamaño de los controles que contiene, se miden en unidades de cuadro de diálogo.  Los valores de cada uno de los controles y del cuadro de diálogo aparecen en la parte inferior derecha de la barra de estado de Visual Studio cuando se seleccionan.  
  
 En la [ventana Propiedades](../Topic/Properties%20Window.md) pueden definirse tres propiedades para especificar en qué parte de la pantalla ha de aparecer un cuadro de diálogo.  La propiedad Center es de tipo Boolean; si se establece su valor en True, el cuadro de diálogo siempre aparecerá centrado en la pantalla.  Si se establece en False, podrán definirse las propiedades XPos y YPos para indicar explícitamente el lugar de la pantalla donde deberá aparecer el cuadro de diálogo.  Las propiedades de posición son valores de distanciamiento con respecto a la esquina superior izquierda del área visible, que se define como {X\=0, Y\=0}.  La posición también depende de la propiedad **Absolute Align**: si es True, las coordenadas serán relativas a la pantalla; si es False, serán relativas a la ventana del propietario del cuadro de diálogo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)