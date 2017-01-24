---
title: "Creating an Icon or Other Image (Image Editor for Icons) | Microsoft Docs"
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
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "bitmaps [C++]"
  - "images [C++], creating"
  - "resource toolbars"
  - "resources [Visual Studio], creating images"
  - "bitmaps [C++], creating"
  - "graphics [C++], creating"
  - "Image editor [C++], creating images"
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating an Icon or Other Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una vez creada una imagen nueva \(mapa de bits, icono, cursor o barra de herramientas\), su aspecto puede personalizarse en el Editor de imágenes.  También se puede crear un mapa de bits nuevo utilizando como modelo una [plantilla](../Topic/How%20to:%20Use%20Resource%20Templates.md).  
  
### Para agregar un recurso de imagen nuevo a un proyecto no administrado de C\+\+  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), haga clic con el botón secundario del mouse en el archivo .rc y elija **Insertar recurso** en el menú contextual.  Si ya dispone de un recurso de imagen en el archivo .rc, como por ejemplo un cursor, sólo tiene que hacer clic con el botón secundario del mouse en la carpeta **Cursor** y seleccionar **Insertar cursor** en el menú contextual.  
  
    > [!NOTE]
    >  **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el [cuadro de diálogo Insertar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), seleccione el tipo de recurso de imagen que desee crear \(**Bitmap**, por ejemplo\) y haga clic en **Nuevo**.  
  
     Si aparece un signo más \(**\+**\) junto al tipo de recurso de imagen del cuadro de diálogo **Insertar recurso**, quiere decir que las plantillas de barra de herramientas están disponibles.  Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **Nuevo**.  
  
### Para agregar un nuevo recurso de imagen a un proyecto en un lenguaje de programación .NET  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en la carpeta del proyecto \(por ejemplo, **WindowsApplication1**\).  
  
2.  En el menú contextual, haga clic en **Agregar** y elija **Agregar nuevo elemento**.  
  
3.  En el panel **Categorías**, expanda la carpeta **Elementos de proyecto local** y elija **Recursos**.  
  
4.  En el panel **Plantillas**, elija el tipo de recurso que desee agregar al proyecto.  
  
     El recurso se agregará al proyecto en el Explorador de soluciones y se abrirá en el [Editor de imágenes](../mfc/image-editor-for-icons.md).  Ahora puede utilizar todas las herramientas disponibles en el Editor de imágenes para modificar la imagen.  Para obtener más información sobre cómo agregar imágenes a un proyecto administrado, vea [Cargar una imagen en tiempo de diseño](../Topic/How%20to:%20Load%20a%20Picture%20Using%20the%20Designer%20\(Windows%20Forms\).md).  
  
    > [!NOTE]
    >  Todos los recursos administrados que vaya a editar deberán estar vinculados.  Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  Para obtener más información, vea [Crear archivos de recursos](../Topic/Creating%20Resource%20Files%20for%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Converting Bitmaps to Toolbars](../mfc/converting-bitmaps-to-toolbars.md)   
 [Creating New Toolbars](../mfc/creating-new-toolbars.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)