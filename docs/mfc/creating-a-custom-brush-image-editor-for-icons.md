---
title: "Creating a Custom Brush (Image Editor for Icons) | Microsoft Docs"
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
  - "colors [C++], brush"
  - "brushes, colors"
  - "brushes, creating custom"
  - "images [C++], creating custom brushes"
  - "graphics [C++], custom brushes"
  - "custom brushes"
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Custom Brush (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un pincel personalizado es una parte rectangular de una imagen que se selecciona y utiliza como si fuera un pincel predefinido del Editor de imágenes.  Todas las operaciones que pueden realizarse en una selección también pueden ejecutarse en un pincel personalizado.  
  
### Para crear un pincel personalizado a partir de parte de una imagen  
  
1.  [Seleccione la parte de la imagen](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md) que desee utilizar como pincel.  
  
2.  Mantenga presionada la tecla **MAYÚS**, haga clic en la selección y arrastre el puntero sobre la imagen.  
  
     \-O bien\-  
  
3.  En el menú **Imagen**, elija **Usar la selección como pincel**.  
  
     La selección se convierte en un pincel personalizado que distribuye los colores que contiene en la imagen.  Se sitúan copias de la selección a lo largo de la trayectoria de arrastre.  Cuanto menor sea la velocidad de arrastre, más copias se crearán.  
  
     **Nota** Al hacer clic en **Usar la selección como pincel** sin seleccionar antes una parte de la imagen se utiliza toda ella como pincel.  El resultado de usar un pincel personalizado también depende de la selección de un [fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 Los píxeles de un pincel personalizado que coincidan con el color de fondo actual normalmente son transparentes: no pintan la imagen.  Este comportamiento puede cambiarse, de forma que los píxeles del color de fondo pinten la imagen existente.  
  
 El pincel personalizado puede utilizarse como un sello o un cliché para crear multitud de efectos especiales.  
  
#### Para dibujar formas de pincel personalizadas con el color de fondo  
  
1.  [Seleccione un fondo opaco o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
2.  [Establezca el color de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) en el color con el que desee dibujar.  
  
3.  Sitúe el pincel personalizado en el lugar donde desee dibujar.  
  
4.  Haga clic con el botón secundario del mouse.  Las regiones opacas del pincel personalizado se dibujan en el color de fondo.  
  
#### Para duplicar o reducir a la mitad el tamaño del pincel personalizado  
  
1.  Presione la tecla **SIGNO MÁS** \(**\+**\) para duplicar el tamaño y la tecla **SIGNO MENOS** \(**–**\) para dividirlo por dos.  
  
#### Para cancelar el pincel personalizado  
  
1.  Presione **ESC** o elija otra herramienta de dibujo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)