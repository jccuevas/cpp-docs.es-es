---
title: "Version Information Editor | Microsoft Docs"
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
  - "vc.editors.version.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Version Information editor, about Version Information editor"
  - "editors, Version Information"
  - "resource editors, Version Information editor"
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Version Information Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La información de versión consta de la identificación del producto y la empresa, un número de versión del producto, y la notificación de copyright y marca comercial. Con el editor de Información de versión, crea y mantiene estos datos, que se almacenan en el recurso de información de versión. Una aplicación no requiere el recurso de información de versión, pero es un lugar útil para recopilar información que identifica la aplicación. También se usa la información de versión por las API de instalación.  
  
 Un recurso de información de versión tiene un bloque superior y uno o más bloques inferiores: un único bloque de información fija en la parte superior y uno o más bloques de información de versión en la parte inferior \(para otros idiomas o juegos de caracteres\). El bloque superior tiene tanto cuadros numéricos editables como listas desplegables seleccionables. Los bloques inferiores solo tienen cuadros de texto editables.  
  
> [!NOTE]
>  El estándar de Windows es tener únicamente un recurso de versión, llamado VS\_VERSION\_INFO.  
  
 El editor de información de versión le permite:  
  
-   [Editar una cadena en un recurso de información de versión.](../mfc/editing-a-string-in-a-version-information-resource.md)  
  
-   [Agregar información de versión para otro idioma \(nuevo bloque de información de versión\).](../mfc/adding-version-information-for-another-language.md)  
  
-   [Eliminar un bloque de información de versión.](../mfc/deleting-a-version-information-block.md)  
  
-   [Obtener acceso a la información de versión desde dentro de su programa.](../mfc/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  Al usar el editor de información de versión, en muchos casos puede hacer clic con el botón secundario para mostrar un menú contextual de comandos específicos de recursos. Por ejemplo, si hace clic mientras señala a una entrada de encabezado de bloque, en el menú contextual se muestra los comandos de nueva información del bloque de versión y eliminar información de bloque de versión.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)   
 [Menús y otros recursos](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)