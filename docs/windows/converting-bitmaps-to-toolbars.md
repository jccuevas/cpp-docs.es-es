---
title: "Converting Bitmaps to Toolbars | Microsoft Docs"
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
  - "bitmaps [C++], converting to toolbars"
  - "Toolbar editor, converting bitmaps"
  - "toolbars [C++], converting bitmaps"
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Converting Bitmaps to Toolbars
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear una barra de herramientas nueva mediante la conversión de un mapa de bits.  El gráfico del mapa de bits convierte las imágenes de los botones de una barra de herramientas.  Normalmente, un mismo mapa de bits contiene varias imágenes de botón, una por cada botón.  Las imágenes pueden tener cualquier tamaño; el valor predeterminado es un ancho de 16 píxeles y el mismo alto que la imagen.  Puede especificar el tamaño de las imágenes de botón en el [cuadro de diálogo Nuevo recurso de la barra de herramientas](../mfc/new-toolbar-resource-dialog-box.md), que se abre al elegir Editor de barras de herramientas en el menú **Imagen** del Editor de imágenes.  
  
### Para convertir un mapa de bits en una barra de herramientas  
  
1.  Abra un recurso de mapa de bits ya existente en el [Editor de imágenes](../mfc/image-editor-for-icons.md).  Si el archivo .rc todavía no contiene el mapa de bits, haga clic con el botón secundario del mouse en el archivo .rc, elija **Importar** en el menú contextual, navegue hasta el mapa de bits que desee agregar al archivo .rc y haga clic en **Abrir**\).  
  
2.  En el menú **Imagen**, elija **Editor de barras de herramientas**.  
  
     Aparecerá el [cuadro de diálogo Nuevo recurso de la barra de herramientas](../mfc/new-toolbar-resource-dialog-box.md).  Puede cambiar el ancho y el alto de las imágenes de iconos para adaptarlos al mapa de bits.  Después se muestra la imagen de la barra de herramientas en el Editor de barras de herramientas.  
  
3.  Para finalizar la conversión, cambie el **ID** de comando del botón en la [ventana Propiedades](../Topic/Properties%20Window.md).  Escriba el nuevo **ID** o selecciónelo en la lista desplegable.  
  
    > [!TIP]
    >  La ventana Propiedades contiene un botón de alfiler en la barra de título.  Al hacer clic en este botón se habilita o deshabilita la opción Ocultar automáticamente para la ventana.  Para recorrer rápidamente todas las propiedades de los botones de la barra de herramientas sin tener que volver a abrir cada ventana de propiedad individual, desactive Ocultar automáticamente, con lo que la ventana Propiedades permanecerá estacionaria.  
  
 También puede cambiar los Id. de comando de la nueva barra de herramientas en la [ventana Propiedades](../Topic/Properties%20Window.md).  Para obtener información sobre cómo editar la nueva barra de herramientas, vea [Crear, mover y editar botones de la barra de herramientas](../mfc/creating-moving-and-editing-toolbar-buttons.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 MFC o ATL  
  
## Vea también  
 [Creating New Toolbars](../mfc/creating-new-toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)