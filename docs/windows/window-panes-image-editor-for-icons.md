---
title: "Window Panes (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
  - "vc.editors.icon"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "graphics editor [C++]"
  - "Image editor [C++], panes"
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Window Panes (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ventana del Editor de imágenes normalmente presenta una imagen en dos paneles separados por una barra divisora.  Una de las vistas presenta la imagen a tamaño real y en la otra está ampliada \(el factor de ampliación predeterminado es 6\).  Las vistas de estos dos paneles se actualizan de forma automática: los cambios efectuados en un panel se muestran inmediatamente en el otro.  Los dos paneles facilitan el trabajo, ya que en la vista ampliada de la imagen pueden distinguirse los píxeles individuales, al tiempo que se observa el efecto del trabajo en la vista a tamaño real de la imagen.  
  
 El panel izquierdo ocupa todo el espacio que necesita \(hasta la mitad de la ventana Imagen\) para mostrar una ampliación 1:1 \(valor predeterminado\) de la imagen.  El panel derecho presenta la imagen ampliada \(ampliación 6:1 de forma predeterminada\).  Se puede [cambiar la ampliación](../mfc/changing-the-magnification-factor-image-editor-for-icons.md) en los paneles utilizando la herramienta **Aumentar** de la [barra de herramientas del Editor de imágenes](../mfc/toolbar-image-editor-for-icons.md) o mediante teclas de aceleración.  
  
 Asimismo, es posible ampliar el panel menor de la ventana del Editor de imágenes para usar los dos paneles de forma que permitan ver dos regiones diferentes de una imagen extensa.  Haga clic en un panel para seleccionarlo.  
  
 El tamaño relativo de los paneles también puede cambiarse, situando el puntero sobre la barra divisora y desplazando ésta a la derecha o la izquierda.  La barra divisora puede desplazarse hasta uno u otro extremo, si se desea trabajar únicamente con uno de los paneles.  
  
 Si el panel del Editor de imágenes se amplía en un factor de 4 o más, se puede [mostrar una cuadrícula de píxeles](../mfc/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) para delimitar los píxeles individuales de la imagen.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)