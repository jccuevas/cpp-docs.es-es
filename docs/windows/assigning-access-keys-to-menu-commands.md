---
title: "Assigning Access Keys to Menu Commands | Microsoft Docs"
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
  - "access keys [C++], checking"
  - "menus, shortcut keys"
  - "keyboard shortcuts [C++], command assignments"
  - "access keys [C++], assigning"
  - "mnemonics, adding to menus"
  - "keyboard shortcuts [C++], uniqueness checking"
  - "mnemonics, uniqueness checking"
  - "Check Mnemonics command"
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Assigning Access Keys to Menu Commands
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede asignar una tecla de acceso, que permite al usuario seleccionar el menú con el teclado, para los menús y comandos de menú.  
  
### Para asignar una tecla de acceso \(método abreviado\) a un comando de menú  
  
1.  Escriba una y comercial \(**&**\) delante de una letra en el nombre del menú o el nombre de comando para especificar esa letra como la tecla de acceso correspondiente. Por ejemplo "&Archivo" define ALT\+A como la tecla de método abreviado para el menú Archivo en las aplicaciones escritas para Microsoft Windows.  
  
     El elemento de menú ofrecerá una indicación visible de que una de las letras tiene asignada una tecla de método abreviado. La letra que sigue a la y comercial aparece subrayada \(depende del sistema operativo\).  
  
    > [!NOTE]
    >  Para asegurarse de que todas las teclas de acceso de un menú son únicas, haga clic con el botón secundario en el menú y elija **Comprobar teclas de acceso** en el menú contextual.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Menu Editor](../mfc/menu-editor.md)