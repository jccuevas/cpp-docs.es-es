---
title: "Drawing Lines or Closed Figures (Image Editor for Icons) | Microsoft Docs"
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
  - "closed figures, drawing"
  - "lines [C++], painting"
  - "lines [C++], drawing"
  - "Image editor [C++], drawing lines"
  - "shapes, drawing"
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Drawing Lines or Closed Figures (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las herramientas de dibujo de líneas y de figuras cerradas del Editor de imágenes funcionan de la misma manera: se sitúa el punto de inserción en un punto y se arrastra hasta otro.  En las líneas, estos puntos son los extremos.  En las figuras cerradas, los puntos son los vértices opuestos de un rectángulo que las limita.  
  
 Las líneas se dibujan con un ancho que viene determinado por la selección del pincel actual, y las figuras enmarcadas se dibujan con un ancho determinado por la selección de ancho actual.  Las líneas y las figuras, tanto las enmarcadas como las rellenas, se dibujan con el color de primer plano actual, si se presiona el botón primario del mouse, o con el color de fondo actual, si se presiona el botón secundario del mouse.  
  
### Para dibujar una línea  
  
1.  En la [barra de herramientas del Editor de imágenes](../mfc/toolbar-image-editor-for-icons.md) \(o en el menú **Imagen**, comando **Herramientas**\), haga clic en la herramienta **Línea**.  
  
2.  Si es necesario, seleccione los colores y un pincel:  
  
    -   En la [paleta Colores](../Topic/Colors%20Window%20\(Image%20Editor%20for%20Icons\).md), haga clic con el botón primario del mouse para seleccionar un color de primer plano o con el botón secundario para seleccionar un color de fondo.  
  
    -   En el [selector de Opciones](../mfc/toolbar-image-editor-for-icons.md), haga clic en la forma que represente el pincel que desea usar.  
  
3.  Coloque el puntero en el punto de inicio de la línea.  
  
4.  Arrastre hasta el extremo de la línea.  
  
### Para dibujar una figura cerrada  
  
1.  En la barra de herramientas del **Editor de imágenes** \(o en el menú **Imagen**, comando **Herramientas**\), haga clic en la herramienta **Dibujo de figuras cerradas**.  
  
     Las herramientas **Dibujo de figuras cerradas** crean las figuras que se indican en sus respectivos botones.  
  
2.  Si es necesario, seleccione los colores y el ancho de línea.  
  
3.  Desplace el puntero a un vértice del área rectangular donde desee dibujar la figura.  
  
4.  Arrastre el puntero hasta el vértice opuesto en la diagonal.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 None  
  
## Vea también  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)