---
title: "Creating a Tool Tip for a Toolbar Button | Microsoft Docs"
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
  - "tool tips [C++], adding to toolbar buttons"
  - "\n in tool tip"
  - "toolbar buttons [C++], tool tips"
  - "buttons [C++], tool tips"
  - "Toolbar editor, creating tool tips"
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Tool Tip for a Toolbar Button
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para crear una información sobre herramientas  
  
1.  Seleccione el botón de la barra de herramientas.  
  
2.  En el campo de la propiedad **Prompt** de la [ventana Propiedades](../Topic/Properties%20Window.md), agregue una descripción del botón para mostrarla en la barra de estado; a continuación del mensaje, agregue \\n y el nombre de la información sobre herramientas.  
  
 Un ejemplo común de una información sobre herramientas es el botón Imprimir de WordPad:  
  
 1.  Abra WordPad.  
  
 2.  Desplace el puntero del mouse sobre el botón de la barra de herramientas **Imprimir**.  
  
 3.  Observe que ahora la palabra 'Imprimir' flota debajo del puntero del mouse.  
  
 4.  Examine la barra de estado \(en la parte inferior de la ventana de Wordpad\); ahora se muestra en ella el texto "Imprime el documento activo".  
  
 'Imprimir' del Paso 3 es el "nombre de la información sobre herramientas" e 'Imprime el documento activo' del Paso 4 es la "descripción del botón para la barra de estado".  
  
 Si desea obtener este efecto por medio del editor de **Barras de herramientas**, establezca la propiedad **Prompt** en **Imprime el documento activo\\nImprimir**.  
  
> [!NOTE]
>  Puede editar el texto del mensaje en la [ventana Propiedades](../Topic/Properties%20Window.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 MFC o ATL  
  
## Vea también  
 [Creating, Moving, and Editing Toolbar Buttons](../mfc/creating-moving-and-editing-toolbar-buttons.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)