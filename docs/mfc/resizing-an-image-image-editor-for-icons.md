---
title: "Resizing an Image (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.image.editing"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], resizing images"
  - "graphics [C++], resizing"
  - "images [C++], resizing"
  - "resizing images"
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resizing an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El comportamiento del Editor de imágenes mientras se cambia el tamaño de una imagen depende de si está [seleccionada](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md) la imagen completa o sólo una parte de ella.  
  
 Si la selección solamente incluye parte de la imagen, el Editor de imágenes reduce la selección, eliminando filas o columnas de píxeles y rellenando las regiones vaciadas con el color de fondo actual, o bien la amplía, duplicando filas o columnas de píxeles.  
  
 Si la selección incluye la imagen completa, el Editor de imágenes amplía y reduce la imagen o bien la recorta y la expande.  
  
 Para cambiar el tamaño de una imagen existen dos mecanismos: los cuadros de tamaño y la [ventana Propiedades](../Topic/Properties%20Window.md).  El tamaño de una imagen completa o de parte de ella puede cambiarse arrastrando los cuadros de tamaño.  Los cuadros de tamaño que pueden arrastrarse son sólidos;  no pueden arrastrarse los cuadros huecos.  La ventana Propiedades sólo permite cambiar el tamaño de la imagen completa, no de una parte seleccionada.  
  
 ![Controladores de tamaño de un mapa de bits](../mfc/media/vcimageeditorsizinghandles.png "vcImageEditorSizingHandles")  
Cuadros de tamaño  
  
> [!NOTE]
>  Si la opción Cuadrícula de mosaico está seleccionadaen la [cuadro de diálogo Configuración de la cuadrícula](../mfc/grid-settings-dialog-box-image-editor-for-icons.md), el nuevo tamaño se ajustará a la siguiente línea de la cuadrícula del mosaico.  Si solamente está seleccionada la opción Cuadrícula de píxeles \(valor predeterminado\), el nuevo tamaño se ajusta al siguiente píxel disponible.  
  
-   [Cambiar el tamaño de una imagen completa](../mfc/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Recortar o ampliar una imagen completa](../mfc/cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Comprimir o ajustar una imagen completa](../mfc/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Comprimir o ajustar parte de una imagen](../mfc/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)