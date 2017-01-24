---
title: "Working with Color (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.image.color"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "images [C++], background colors"
  - "Image editor [C++], Colors Palette"
  - "colors [C++], image"
  - "Colors Palette, Image editor"
  - "palettes, Image editor colors"
  - "foreground colors, Image editor"
  - "colors [C++]"
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Working with Color (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Editor de imágenes contiene numerosas características que controlan de forma específica y personalizan los colores.  Se puede definir un color de primer plano o de fondo, rellenar áreas delimitadas con un color o seleccionar un color de una imagen para usarlo como el color de primer plano o de fondo actual.  Las herramientas de la [barra de herramientas del Editor de imágenes](../mfc/toolbar-image-editor-for-icons.md) pueden utilizarse junto con la paleta de colores de la [ventana Colores](../Topic/Colors%20Window%20\(Image%20Editor%20for%20Icons\).md) para crear imágenes.  
  
 Todos los colores de las imágenes monocromáticas y en 16 colores se muestran en la paleta Colores de la ventana Colores.  Además de los 16 colores estándar, puede crear sus propios colores personalizados.  Los cambios realizados en los colores de la paleta se actualizan inmediatamente en el color correspondiente de la imagen.  
  
 Cuando se trabaja con imágenes de iconos y cursores de 256 colores, se utiliza la propiedad Colors de la [ventana Propiedades](../Topic/Properties%20Window.md).  Para obtener más información, vea [Crear un nuevo icono o cursor de 256 colores](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).  
  
> [!NOTE]
>  Con el Editor de imágenes, puede ver imágenes de 32 bits, pero no puede modificarlas.  
  
 También pueden crearse imágenes en color verdadero.  No obstante, no se muestran ejemplos en color verdadero en la paleta completa de la ventana Colores; aparecen solamente en el área de indicador del color de primer plano o de fondo.  Los colores verdaderos se crean utilizando el [cuadro de diálogo Selector de colores](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md).  Para obtener más información, vea [Personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 Las paletas de colores personalizadas pueden guardarse en el disco para utilizarlas cuando se necesiten.  La paleta de colores utilizada en último lugar se guarda en el Registro y se carga de forma automática la siguiente vez que se inicia Visual Studio.  
  
-   [Seleccionar el color de primer plano y el color de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [Llenar un área delimitada de una imagen con un color](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [Seleccionar un color de una imagen para utilizarlo en otro sitio](../Topic/Picking%20up%20a%20Color%20from%20an%20Image%20to%20Use%20Elsewhere%20\(Image%20Editor%20for%20Icons\).md)  
  
-   [Elegir un fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [Invertir los colores de una selección](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [Personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [Guardar y cargar diferentes paletas de colores](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [Ventana Colores](../Topic/Colors%20Window%20\(Image%20Editor%20for%20Icons\).md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Recursos](_win32_Resources)