---
title: "Adding Values to a Combo Box Control | Microsoft Docs"
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
  - "vc.editors.dialog.combo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combo boxes [C++], Data property"
  - "controls [Visual Studio], testing values in combo boxes"
  - "combo boxes [C++], adding values"
  - "combo boxes [C++], previewing values"
  - "controls [C++], testing values in combo boxes"
  - "Data property"
  - "combo boxes [C++], testing values"
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Values to a Combo Box Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se pueden agregar valores a un control de cuadro combinado siempre y cuando esté abierto el Editor de cuadros de diálogo.  
  
> [!TIP]
>  Es conveniente agregar todos los valores al cuadro combinado *antes* de definir su tamaño en el Editor de cuadros de diálogo ya que, de lo contrario, podría truncarse el texto que debería aparecer en el cuadro combinado.  
  
#### Para especificar valores en un control de cuadro combinado  
  
1.  Seleccione el control de cuadro combinado haciendo clic en él.  
  
2.  En la [ventana Propiedades](../Topic/Properties%20Window.md), desplácese a la propiedad **Data**.  
  
    > [!NOTE]
    >  Si las propiedades se muestran agrupadas por tipo, **Data** aparecerá dentro de las propiedades **Varios**.  
  
3.  Haga clic en el área de valores de la propiedad **Data** y escriba los valores de los datos, separados por signos de punto y coma.  
  
    > [!NOTE]
    >  No incluya espacios entre los valores, pues podrían afectar al orden alfabético de la lista desplegable.  
  
4.  Haga clic en **Entrar** cuando termine de agregar valores.  
  
 Para obtener más información sobre cómo aumentar de tamaño la parte desplegable de un cuadro combinado, vea [Establecer el tamaño de un cuadro combinado y de su lista desplegable](../mfc/setting-the-size-of-the-combo-box-and-its-drop-down-list.md).  
  
> [!NOTE]
>  No pueden agregarse valores a proyectos Win32 mediante este procedimiento \(la propiedad **Data** aparece atenuada en dichos proyectos\).  Al carecer los proyectos Win32 de bibliotecas para agregar esta función, los valores de un cuadro combinado en un proyecto Win32 deberán agregarse mediante programación.  
  
#### Para comprobar la apariencia de los valores de un cuadro combinado  
  
1.  Tras especificar los valores en la propiedad **Data**, haga clic en el botón **Probar** de la [barra de herramientas del Editor de cuadros de diálogo](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
     Pruebe a desplazarse por la lista de valores completa.  Los valores se mostrarán tal cual se hayan escrito en la propiedad **Data** de la ventana Propiedades.  No se comprobará ni la ortografía ni las mayúsculas o minúsculas.  
  
     Presione ESC para regresar al Editor de cuadros de diálogo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)