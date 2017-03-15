---
title: "Creating New Toolbars | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.toolbar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "toolbars [C++], creating"
  - "Toolbar editor, creating new toolbars"
  - "Insert Resource"
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creating New Toolbars
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para crear una barra de herramientas nueva  
  
1.  En la **Vista de recursos**, haga clic con el botón secundario del mouse en el archivo .rc y elija **Agregar recurso** en el menú contextual.  Si ya dispone de una barra de herramientas en el archivo .rc, sólo tiene que hacer clic con el botón secundario del mouse en la carpeta **Toolbar** y seleccionar **Insertar Toolbar** en el menú contextual\).  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el cuadro de diálogo **Agregar recurso**, seleccione **Toolbar** en la lista **Tipo de recurso** y haga clic en **Nuevo**.  
  
     Si aparece un signo más \(\+\) junto al tipo de recurso **Toolbar**, quiere decir que están disponibles plantillas de barra de herramientas.  Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **Nuevo**.  
  
     \-O bien\-  
  
3.  [Convierta un mapa de bits existente en una barra de herramientas](../mfc/converting-bitmaps-to-toolbars.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 MFC o ATL  
  
## Vea también  
 [Toolbar Editor](../mfc/toolbar-editor.md)