---
title: "Aligning Controls on a Guide | Microsoft Docs"
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
  - "DLUs (dialog units)"
  - "controls [C++], aligning"
  - "Dialog editor, snap to guides"
  - "guides, tick mark interval"
  - "dialog box controls, placement"
  - "guides, aligning controls"
  - "dialog units (DLUs)"
  - "snap to guides (Dialog editor)"
  - "controls [C++], sizing"
  - "tick mark interval in Dialog editor"
  - "controls [C++], snap to guides/grid"
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aligning Controls on a Guide
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los cuadros de tamaño de los controles se ajustan a las guías cuando los controles se desplazan, asimismo, las guías se ajustan a los controles \(si previamente no había controles ajustados a la guía\).  Cuando se desplaza una guía, los controles ajustados a ella también se desplazan.  Los controles ajustados a varias guías cambian de tamaño cuando se desplaza una de ellas.  
  
 Las marcas de paso de las reglas, que determinan el espaciado de las guías y los controles, se definen en unidades de cuadro de diálogo \(DLU\).  Las unidades de cuadro de diálogo se basan en el tamaño de la fuente del cuadro de diálogo, normalmente MS Shell Dlg de 8 puntos.  Una DLU horizontal equivale al ancho medio de la fuente del cuadro de diálogo dividido por cuatro.  Una unidad de cuadro de diálogo vertical equivale al alto medio del cuadro de diálogo dividido por cuatro.  
  
### Para establecer el tamaño de un grupo de controles con guías  
  
1.  Ajuste un lado del control \(o controles\) a una guía.  
  
2.  Arrastre una guía al otro lado del control \(o controles\).  
  
     Si fuera necesario \(en el caso de varios controles\), establezca el tamaño de cada uno de los controles de forma que se ajuste a la segunda guía.  
  
3.  Mueva una de las guías para establecer el tamaño del control \(o controles\).  
  
### Para cambiar los intervalos de las marcas de paso  
  
1.  En el menú **Formato**, elija **Configuración de las guías**.  
  
2.  En el [cuadro de diálogo Configuración de las guías](../mfc/guide-settings-dialog-box.md), en el campo **Espaciado de cuadrícula**, especifique un ancho y alto nuevos, en unidades de cuadro de diálogo \(DLU\).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Dialog Editor States \(Guides and Grids\)](../mfc/dialog-editor-states-guides-and-grids.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)