---
title: "Creating Transparent or Inverse Regions in Device Images (Image Editor for Icons) | Microsoft Docs"
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
  - "cursors [C++], screen regions"
  - "inverse colors, device images"
  - "transparent regions, device images"
  - "transparency, device images"
  - "Image editor [C++], device images"
  - "inverse regions, device images"
  - "cursors [C++], transparent regions"
  - "screen colors"
  - "regions, transparent"
  - "icons [C++], transparent regions"
  - "display devices, transparent and screen regions"
  - "transparent regions in devices"
  - "regions, inverse"
  - "colors [C++], Image editor"
  - "device projects, transparent images"
  - "icons [C++], screen regions"
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating Transparent or Inverse Regions in Device Images (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el [Editor de imágenes](../mfc/image-editor-for-icons.md), la imagen inicial de icono o el cursor tiene el atributo transparente.  Aunque las imágenes de icono y cursor son rectangulares, muchas no lo parecen, porque partes de la imagen son transparentes; la imagen subyacente en la pantalla puede verse a través del icono o el cursor.  Cuando se arrastra un icono, partes de su imagen pueden aparecer en color inverso.  Este efecto puede crearse estableciendo el color de la pantalla y el inverso en la [ventana Colores](../Topic/Colors%20Window%20\(Image%20Editor%20for%20Icons\).md).  
  
 Los colores de pantalla e inverso aplicados a los iconos y cursores dan forma y color a la imagen derivada o designan zonas inversas.  Los colores indican las partes de la imagen que poseen estos atributos.  Los colores que representan los atributos de color de la pantalla y color inverso pueden cambiarse durante la edición.  Estos cambios no afectan al aspecto del icono o el cursor en la aplicación.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para crear zonas transparentes o inversas  
  
1.  En la ventana **Colores**, haga clic en el selector de **Color de pantalla** o de **Color inverso**.  
  
2.  Aplique el color de pantalla o el color inverso a la imagen utilizando una herramienta de dibujo.  Para obtener más información sobre las herramientas de dibujo, vea [Using a Drawing Tool](../mfc/using-a-drawing-tool-image-editor-for-icons.md).  
  
### Para cambiar el color de pantalla o el inverso  
  
1.  Seleccione el selector de **Color de pantalla** o **Color inverso**.  
  
2.  Elija un color en la paleta **Colores** de la ventana **Colores**.  
  
     Se designa automáticamente el color complementario para el otro selector.  
  
    > [!TIP]
    >  Un doble clic en el selector de Color de pantalla o Color inverso abre el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)