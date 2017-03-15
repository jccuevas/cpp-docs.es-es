---
title: "Nuevo recurso de la barra de herramientas (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.newtoolbarresource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Nuevo recurso de la barra de herramientas (cuadro de diálogo)"
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Nuevo recurso de la barra de herramientas (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El cuadro de diálogo Nuevo recurso de la barra de herramientas permite especificar el ancho y el alto de los botones que se agregan a un recurso de barra de herramientas.  El tamaño predeterminado es de 16 x 15 píxeles.  
  
 Un mapa de bits utilizado para crear una barra de herramientas tiene un ancho máximo de 2048.  Por tanto, si se establece **Ancho de botón** en 512, solo se podrán incluir cuatro botones.  Si lo establece en 513, sólo podrá contar con tres botones.  
  
 **Ancho de botón**  
 Proporciona un espacio para especificar el ancho de los botones de la barra de herramientas que se convierten a partir de un recurso de mapa de bits en un recurso de barra de herramientas.  Las imágenes se recortan al ancho y alto especificados, y los colores se ajustan a los colores de la barra de herramientas estándar \(16\).  
  
 **Alto de botón**  
 Proporciona un espacio para especificar el alto de los botones de la barra de herramientas que se convierten a partir de un recurso de mapa de bits en un recurso de barra de herramientas.  Las imágenes se recortan al ancho y alto especificados, y los colores se ajustan a los colores de la barra de herramientas estándar \(16\).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 MFC o ATL  
  
## Vea también  
 [Toolbar Button Properties](../mfc/toolbar-button-properties.md)   
 [Converting Bitmaps to Toolbars](../mfc/converting-bitmaps-to-toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)