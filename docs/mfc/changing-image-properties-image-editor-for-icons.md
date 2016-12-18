---
title: "Changing Image Properties (Image Editor for Icons) | Microsoft Docs"
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
  - "images [C++], properties"
  - "Image editor [C++], Properties window"
  - "Image editor [C++], image properties"
  - "Properties window, image editor"
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing Image Properties (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las propiedades de una imagen pueden definirse o modificarse en la [ventana Propiedades](../Topic/Properties%20Window.md).  
  
### Para cambiar las propiedades de una imagen  
  
1.  Abra la imagenen la **Editor de imágenes**.  
  
2.  En la ventana **Propiedades**, cambie las propiedades que desee de la imagen.  
  
    |Propiedad.|Descripción|  
    |----------------|-----------------|  
    |**Colors**|Especifica la combinación de colores de la imagen.  Seleccione Monocromático, 16, 256 o Color verdadero.  Si la imagen se ha dibujado con una paleta de 16 colores, la selección de Monocromático causa la sustitución del negro y el blanco por los colores de la imagen.  El contraste no siempre se mantiene: por ejemplo, las partes adyacentes de los colores rojo y verde se convierten en negro.|  
    |**Filename**|Especifica el nombre del archivo de imagen.  De forma predeterminada, Visual Studio asigna un nombre de archivo base que crea quitando los cuatro primeros caracteres \("IDB\_"\) del identificador de recursos predeterminado \(IDB\_BITMAP1\) y agregando la extensión correspondiente.  El nombre del archivo de imagen del ejemplo sería BITMAP1.bmp.  Puede cambiar este nombre a MIBITMAP1.bmp.|  
    |**Alto**|Establece el alto de la imagen \(en píxeles\).  El valor predeterminado es 48.  La imagen se recorta, o bien se agrega espacio en blanco por debajo de ella.|  
    |**Id.**|Establece el identificador de recursos.  Para una imagen, Microsoft Visual Studio asigna de forma predeterminada el siguiente identificador disponible de una serie: IDB\_BITMAP1, IDB\_BITMAP2, etc.  Se utilizan nombres similares para los iconos y los cursores.|  
    |**Palette**|Cambia las propiedades del color.  Haga doble clic para seleccionar un color y abrir el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md).  El color se define especificando valores RGB o HSL en los cuadros de texto apropiados.|  
    |**SaveCompressed**|Indica si la imagen está en formato comprimido.  Esta propiedad es de sólo lectura.  Visual Studio no permite guardar imágenes en formato comprimido, por lo que, para cualquier imagen creada en Visual Studio, esta propiedad tiene el valor **False**.  Si se abre una imagen comprimida \(creada en otro programa\) en Visual Studio, esta propiedad presentará el valor **True**.  Si se guarda una imagen comprimida en Visual Studio, ésta se descomprime y la propiedad vuelve a recibir el valor **False**.|  
    |**Ancho**|Establece el ancho de la imagen \(en píxeles\).  El valor predeterminado para los mapas de bits es 48.  La imagen se recorta, o bien se agrega espacio en blanco a su derecha.|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)