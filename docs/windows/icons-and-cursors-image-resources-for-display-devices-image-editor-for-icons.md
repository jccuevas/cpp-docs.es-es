---
title: "Icons and Cursors: Image Resources for Display Devices (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], creating"
  - "image resources, display devices"
  - "icons [C++], creating"
  - "cursors [C++], types"
  - "icons [C++]"
  - "Image editor [C++], icons and cursors"
  - "cursors [C++]"
  - "display devices, creating icons for"
  - "cursors [C++], hot spots"
  - "icons [C++], types"
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Icons and Cursors: Image Resources for Display Devices (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los iconos y cursores son recursos gráficos que pueden contener varias imágenes de diferentes tamaños y combinaciones de colores para distintos tipos de dispositivos de pantalla. Además, un cursor tiene una "zona activa", la ubicación que Windows usa para realizar un seguimiento de su posición. Tanto los iconos como los cursores se crean y se editan en el editor de imágenes, al igual que los mapas de bits y otras imágenes.  
  
 Al crear un icono o cursor nuevo, el editor de imágenes crea primero una imagen de un tipo estándar. La imagen se rellena inicialmente con el color de la pantalla \(transparente\). Si la imagen es un cursor, la zona activa es inicialmente la esquina superior izquierda \(coordenadas 0,0\).  
  
 De forma predeterminada, el editor de imágenes admite la creación de imágenes adicionales para los dispositivos que se muestran en la tabla siguiente. Puede crear imágenes para otros dispositivos escribiendo parámetros de ancho, alto y número de colores en el [cuadro de diálogo Imagen personalizada](../mfc/custom-image-dialog-box-image-editor-for-icons.md).  
  
> [!NOTE]
>  Con el Editor de imágenes, se pueden ver imágenes de 32 bits, pero no se pueden editar.  
  
|Color|Ancho \(píxeles\)|Alto \(píxeles\)|  
|-----------|-----------------------|----------------------|  
|Monocromático|16|16|  
|Monocromático|32|32|  
|Monocromático|48|48|  
|Monocromático|64|64|  
|Monocromático|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [Crear una imagen de dispositivo nueva \(icono o cursor\)](../mfc/creating-a-device-image-image-editor-for-icons.md)  
  
-   [Agregar una imagen para otro dispositivo de presentación](../mfc/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [Copiar una imagen de dispositivo](../mfc/copying-a-device-image-image-editor-for-icons.md)  
  
-   [Eliminar una imagen de dispositivo](../mfc/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [Crear zonas transparentes o inversas en las imágenes de dispositivo](../mfc/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [Crear un nuevo icono o cursor de 256 colores](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [Establecer la zona activa del cursor](../mfc/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Ninguna  
  
## Vea también  
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Iconos](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [Cursores](http://msdn.microsoft.com/library/windows/desktop/ms646970)