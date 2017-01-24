---
title: "Editing Parts of an Image (Image Editor for Icons) | Microsoft Docs"
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
  - "Image editor [C++], editing images"
  - "Clipboard [C++], pasting"
  - "images [C++], editing"
  - "images [C++], deleting selected parts"
  - "images [C++], copying selected parts"
  - "images [C++], moving selected parts"
  - "images [C++], dragging and replicating selected parts"
  - "images [C++], pasting into"
  - "graphics [C++], editing"
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Editing Parts of an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una [selección](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md) pueden realizarse las operaciones de edición normales, es decir, cortar, copiar, borrar y mover, sea la selección la imagen completa o solamente una parte de ella.  Como el editor de Imágenes utiliza el Portapapeles de Windows, pueden transferirse imágenes entre el editor de Imágenes y otras aplicaciones para Windows.  
  
 Asimismo, el tamaño de la selección puede cambiarse, incluya a la imagen completa o solamente una parte de ella.  
  
### Para cortar la selección actual y moverla al Portapapeles  
  
1.  En el menú **Edición**, haga clic en **Cortar**.  
  
### Para copiar la selección  
  
1.  Sitúe el puntero dentro del borde de la selección o en cualquier posición sobre él excepto los cuadros de tamaño.  
  
2.  Mantenga presionada la tecla **CTRL** mientras arrastra la selección a otro lugar.  El área de la selección original no varía.  
  
3.  Para copiar la selección en la imagen, en su ubicación actual, haga clic fuera del cursor de selección.  
  
### Para pegar el contenido del Portapapeles en una imagen  
  
1.  En el menú **Edición**, elija **Pegar**.  
  
     Aparece el contenido del Portapapeles, rodeado por el borde de selección, en la esquina superior izquierda del panel.  
  
2.  Sitúe el puntero dentro del borde de selección y arrastre la imagen a la posición que desee en la imagen.  
  
3.  Para fijar la imagen en su nueva ubicación, haga clic fuera del borde de selección.  
  
### Para eliminar la selección actual sin moverla al Portapapeles  
  
1.  En el menú **Edición**, elija **Eliminar**.  
  
     El área original de la selección se rellena con el color de fondo actual.  
  
    > [!NOTE]
    >  Los comandos Cortar, Copiar, Pegar y Eliminar están disponibles cuando se hace clic con el botón secundario del mouse en la ventana Vista de recursos.  
  
### Para mover la selección  
  
1.  Sitúe el puntero dentro del borde de la selección o en cualquier posición sobre él excepto los cuadros de tamaño.  
  
2.  Arrastre la selección hasta su nueva ubicación.  
  
3.  Para delimitar la selección en la imagen en su nueva ubicación, haga clic fuera del borde de selección.  
  
 Para obtener más información sobre cómo dibujar con una selección, vea [Crear un pincel personalizado](../mfc/creating-a-custom-brush-image-editor-for-icons.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)