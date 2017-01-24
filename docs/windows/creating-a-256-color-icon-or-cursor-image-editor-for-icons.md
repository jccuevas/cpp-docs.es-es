---
title: "Creating a 256-Color Icon or Cursor (Image Editor for Icons) | Microsoft Docs"
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
helpviewer_keywords: 
  - "256-color palette"
  - "cursors, color"
  - "colors, icons"
  - "colors, cursors"
  - "icons, color"
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a 256-Color Icon or Cursor (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tamaño de los iconos y cursores puede ampliarse \(64 x 64\) en el Editor de imágenes, y puede elegirse un color de una paleta de 256 colores.  Tras crear el recurso, se selecciona un estilo de imagen del dispositivo.  
  
### Para crear un icono o cursor de 256 colores  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), haga clic con el botón secundario del mouse en el archivo .rc y elija **Insertar recurso** en el menú contextual.  Si ya dispone de un recurso de imagen en el archivo .rc, como por ejemplo un cursor, sólo tiene que hacer clic con el botón secundario del mouse en la carpeta **Cursor** y seleccionar **Insertar cursor** en el menú contextual.  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el [cuadro de diálogo Insertar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), seleccione **Icon** o **Cursor** y haga clic en **Nuevo**.  
  
3.  En el menú **Imagen**, haga clic en **Nueva imagen de dispositivo**.  
  
4.  Seleccione el estilo de imagen de 256 colores que desee.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 None  
  
## Vea también  
 [Using the 256\-Color Palette](../mfc/using-the-256-color-palette-image-editor-for-icons.md)   
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)