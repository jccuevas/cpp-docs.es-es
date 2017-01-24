---
title: "Associating Menu Commands with Status Bar Text in MFC Applications | Microsoft Docs"
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
  - "status bars, associating menu items"
  - "menus, status bar text"
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associating Menu Commands with Status Bar Text in MFC Applications
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La aplicación puede mostrar texto descriptivo para cada uno de los comandos de menú que puede seleccionar un usuario. Para ello, asigne una cadena de texto a cada comando de menú mediante la propiedad **Prompt** de la ventana Propiedades. Si tiene una cadena en la [tabla de cadenas](../mfc/string-editor.md) cuyo id. es igual que el comando, una aplicación MFC mostrará automáticamente este recurso de cadena en la barra de estado de la aplicación en ejecución cuando un usuario se desplace sobre un elemento de menú.  
  
### Para asociar un comando de menú a una cadena de texto de la barra de estado  
  
1.  En el editor de **menús**, seleccione el comando de menú.  
  
2.  En la [ventana Propiedades](../Topic/Properties%20Window.md), escriba el texto de la barra de estado asociado en el cuadro **Prompt**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 MFC  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)   
 [Adding Commands to a Menu](../Topic/Adding%20Commands%20to%20a%20Menu.md)   
 [Menu Editor](../mfc/menu-editor.md)