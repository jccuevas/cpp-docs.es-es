---
title: "Creating a Device Image (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.icon"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], creating"
  - "icons [C++], creating"
  - "display devices"
  - "display devices, creating image"
  - "images [C++], creating for display devices"
  - "icons [C++], inserting"
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Device Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea un recurso nuevo de icono o de cursor, el Editor de imágenes crea en primer lugar una imagen con un estilo concreto \(32 x 32, 16 colores para los iconos y 32 x 32, monocromático para los cursores\).  Después pueden agregarse imágenes de tamaños y estilos diferentes al icono o cursor inicial y editarse cada imagen adicional, según se necesite, para los distintos dispositivos de presentación.  También puede editar una imagen realizando una operación de cortar y pegar a partir de un tipo de imagen existente o de un mapa de bits creado en un programa de gráficos.  Para obtener más información sobre las dimensiones de los iconos que Windows utiliza, vea [Iconos](_win32_Icons_cpp) en la documentación del SDK de Windows.  
  
 Cuando se abre el recurso de icono o cursoren la [Editor de imágenes](../mfc/image-editor-for-icons.md), de forma predeterminada se abre la imagen más parecida al dispositivo de presentación actual.  
  
### Para crear un nuevo icono o cursor  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), haga clic con el botón secundario del mouse en el archivo .rc y elija **Insertar recurso** en el menú contextual.  Si ya dispone de un recurso de imagen en el archivo .rc, como un cursor, sólo tiene que hacer clic con el botón secundario del mouse en la carpeta **Cursor** y seleccionar **Insertar cursor** en el menú contextual.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el cuadro de diálogo [Insertar recurso](../Topic/Add%20Resource%20Dialog%20Box.md), seleccione **Icono** o **Cursor** y haga clic en **Nuevo**.  En el caso de los iconos, se crea un recurso de icono con un icono de 32 x 32 y 16 colores.  En el caso de los cursores, se crea una imagen monocromática \(2 colores\) de 32 x 32.  
  
     Si aparece un signo más \(**\+**\) junto al tipo de recurso de imagen del cuadro de diálogo **Insertar recurso**, quiere decir que las plantillas de barra de herramientas están disponibles.  Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **Nuevo**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 None  
  
## Vea también  
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)