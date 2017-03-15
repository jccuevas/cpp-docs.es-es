---
title: "Selecting an Area of an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "Image editor [C++], image selection"
  - "Image editor [C++], selecting images"
  - "images [C++], selecting"
  - "cursors [C++], selecting areas of"
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Selecting an Area of an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las herramientas de selección permiten seleccionar un área de una imagen que después se corta, copia, borra, cambia de tamaño, invierte o mueve.  La herramienta **Selección del rectángulo** permite definir y seleccionar una región rectangular de la imagen.  Con la herramienta **Selección irregular** se puede dibujar a mano alzada el contorno del área que se desea seleccionar para las operaciones de cortar, copiar o de otra clase.  
  
> [!NOTE]
>  Vea las herramientas **Seleccionar rectángulo** y **Selección irregular** que se muestran en la [barra de herramientas del Editor de imágenes](../mfc/toolbar-image-editor-for-icons.md) o vea la información sobre herramientas asociada a cada botón de la barra de herramientas del **Editor de imágenes**.  
  
 También se puede crear un pincel personalizado a partir de una selección.  Para obtener más información, vea [Crear un pincel personalizado](../mfc/creating-a-custom-brush-image-editor-for-icons.md).  
  
### Para seleccionar un área de una imagen  
  
1.  En la barra de herramientas del **Editor de imágenes** \(o en el menú **Imagen**, comando **Herramientas**\), haga clic en la herramienta que desee utilizar.  
  
2.  Desplace el punto de inserción a uno de los vértices del área de la imagen que desee seleccionar.  Aparece un puntero de líneas en cruz cuando el punto de inserción se encuentra sobre la imagen.  
  
3.  Arrastre el punto de inserción hasta el vértice opuesto del área que desea seleccionar.  Se muestran en un rectángulo los píxeles que se seleccionarán.  Todos los píxeles que contiene el rectángulo, incluidos los que se encuentran debajo de él, se incluyen en la selección.  
  
4.  Suelte el botón del mouse.  El borde de selección encierra el área seleccionada.  
  
### Para seleccionar toda la imagen  
  
1.  Haga clic en la imagen, fuera de la selección actual.  El foco del borde de selección cambia y encierra otra vez a toda la imagen.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)