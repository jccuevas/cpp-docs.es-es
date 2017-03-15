---
title: "Toolbar Button Properties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size, toolbar buttons"
  - "toolbar buttons (in Toolbar editor), setting properties"
  - "Toolbar editor, toolbar button properties"
  - "status bars, active toolbar button text"
  - "command IDs, toolbar buttons"
  - "width, toolbar buttons"
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Toolbar Button Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las propiedades de un botón de la barra de herramientas son:  
  
|Propiedad.|Descripción|  
|----------------|-----------------|  
|**Id.**|Define el Id. del botón.  La lista desplegable proporciona nombres **ID** comunes.|  
|**Ancho**|Establece el ancho del botón.  Se recomienda un alto de 16 píxeles.|  
|**Alto**|Establece el alto del botón.  Tenga en cuenta que el alto de un botón cambia el alto de todos los botones de la barra de herramientas.  Se recomienda un alto de 15 píxeles.|  
|**Prompt**|Define el mensaje que se mostrará en la barra de estado.  Si agrega \\n y un nombre, se agregará información sobre herramientas al botón de la barra.  Para obtener más información, vea [Crear información sobre herramientas](../mfc/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Width** y **Height** se aplican a todos los botones.  Un mapa de bits utilizado para crear una barra de herramientas tiene un ancho máximo de 2048.  Por tanto, si se establece el ancho de botón en 512, solo se podrán incluir cuatro botones; si se establece en 513, solo se podrá contar con tres botones.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 MFC o ATL  
  
## Vea también  
 [Changing the Properties of a Toolbar Button](../mfc/changing-the-properties-of-a-toolbar-button.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)