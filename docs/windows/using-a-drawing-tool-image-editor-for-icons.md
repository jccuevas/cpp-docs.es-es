---
title: "Using a Drawing Tool (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.image.drawing"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], selecting drawing tools"
  - "Image editor [C++], toolbar"
  - "drawing tools"
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using a Drawing Tool (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las herramientas de dibujo a mano alzada y de borrado del Editor de imágenes funcionan de la misma manera: se selecciona una herramienta y, si es necesario, se [seleccionan los colores de primer plano y de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) y las opciones de tamaño y de forma.  Después se sitúa el puntero en la imagen y se hace clic o se arrastra para dibujar o borrar.  
  
 Cuando está seleccionada la herramienta **Borrador**, **Pincel** o **Aerógrafo**, el selector de opciones muestra las opciones correspondientes a la herramienta pertinente.  
  
> [!TIP]
>  En lugar de usar la herramienta **Borrador**, puede que sea más práctico dibujar en el color de fondo con una de las herramientas de dibujo.  
  
 Puede seleccionar herramientas de dibujo en la barra de herramientas del **Editor de imágenes** o en el menú **Imagen**.  
  
### Para seleccionar y utilizar una herramienta de dibujo de la barra de herramientas del Editor de imágenes  
  
1.  Haga clic en un botón de la barra de herramientas del **Editor de imágenes**.  
  
    -   Al presionar el botón primario del mouse la herramienta **Borrador** pinta la imagen con el color de fondo actual.  
  
    -   La herramienta **Lápiz** dibuja a mano alzada con un ancho constante de un píxel.  
  
    -   El **selector de opciones determina la forma y el tamaño de la herramienta Pincel**.  
  
    -   La herramienta **Aerógrafo** distribuye de forma aleatoria píxeles de color en torno al centro del pincel.  
  
        > [!TIP]
        >  Cuando se desplaza el cursor sobre los botones de la [barra de herramientas del Editor de imágenes](../mfc/toolbar-image-editor-for-icons.md), aparece la información sobre herramientas.  Estas sugerencias ayudan a identificar los botones que se mencionan en este documento.  
  
2.  Si es necesario, seleccione los colores y un pincel:  
  
    -   En la [paleta Colores](../Topic/Colors%20Window%20\(Image%20Editor%20for%20Icons\).md), haga clic con el botón primario del mouse para seleccionar un color de primer plano o con el botón secundario para seleccionar un color de fondo.  
  
    -   En el [selector de Opciones](../mfc/toolbar-image-editor-for-icons.md), haga clic en la forma que represente el pincel que desea usar.  
  
3.  Señale al lugar de la imagen donde desee empezar a dibujar o pintar.  La forma del puntero cambia conforme a la herramienta seleccionada.  
  
4.  Presione el botón primario del mouse \(para el color de primer plano\) o el botón secundario \(para el color de fondo\) y manténgalo presionado mientras dibuja.  
  
### Para seleccionar y utilizar una herramienta de dibujo del menú Imagen  
  
1.  Haga clic en el menú **Imagen** y seleccione el comando **Herramientas**.  
  
2.  En el submenú en cascada, elija la herramienta que desee utilizar.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)