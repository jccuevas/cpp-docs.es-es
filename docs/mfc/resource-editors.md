---
title: "Resource Editors | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.editors.resource"
  - "vc.resvw.resource.editors"
  - "vs.resvw.resource.editors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "editors [C++], resource"
  - "editors [C++]"
  - "resource editors"
  - "Windows [C++], application resource editing"
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resource Editors
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un editor de recursos es un entorno especializado para la creación o la modificación de los recursos que se incluyen en un proyecto de Visual Studio. Los editores de recursos de Visual Studio comparten técnicas e interfaces que ayudan a crear y modificar recursos de la aplicación de forma rápida y sencilla. Los editores de recursos permiten [ver y editar recursos en el editor adecuado](../mfc/viewing-and-editing-resources-in-a-resource-editor.md) y [obtener una vista previa de los recursos](../mfc/previewing-resources.md).  
  
 Al crear o abrir un recurso, se abre automáticamente el editor correspondiente.  
  
 **Nota**: dado que los proyectos administrados no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Se puede usar el [Editor de imágenes](../mfc/image-editor-for-icons.md) y el [Editor binario](../mfc/binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
|Use...|Para editar...|  
|------------|--------------------|  
|[Editor de aceleradores](../mfc/accelerator-editor.md)|Tablas de aceleradores en proyectos de Visual C\+\+.|  
|[Editor binario](../mfc/binary-editor.md)|Información de datos binarios y recursos personalizados en proyectos de Visual C\+\+, Visual Basic o Visual C\#.|  
|[Editor de cuadros de diálogo](../mfc/dialog-editor.md)|Cuadros de diálogo en proyectos de Visual C\+\+.|  
|[Diseñador de HTML](../Topic/HTML%20Designer.md)|Páginas HTML en la vista Diseño y la vista HTML. Advertencia: no se pueden hacer cambios en las páginas HTML que se encuentran en archivos EXE o DLL porque tales cambios no se importan de nuevo al archivo EXE o DLL.|  
|[Editor de imágenes](../mfc/image-editor-for-icons.md)|Mapas de bits, iconos, cursores y otros archivos de imagen en proyectos de Visual C\+\+, Visual Basic o Visual C\#.|  
|[Editor de menús](../mfc/menu-editor.md)|Recursos de menús en proyectos de Visual C\+\+.|  
|[Editor de Ribbon](../mfc/ribbon-designer-mfc.md)|Recursos de cinta de opciones en proyectos de MFC.|  
|[Editor de cadenas](../mfc/string-editor.md)|Tablas de cadenas en proyectos de Visual C\+\+.|  
|[Editor de barras de herramientas](../mfc/toolbar-editor.md)|Recursos de barras de herramientas en proyectos de Visual C\+\+. El editor de barras de herramientas es parte del editor de imágenes.|  
|[Editor de la información de versión](../mfc/version-information-editor.md)|Información de versión en proyectos de Visual C\+\+.|  
  
## Requisitos  
 Ninguno  
  
## Vea también  
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Menús y otros recursos](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)