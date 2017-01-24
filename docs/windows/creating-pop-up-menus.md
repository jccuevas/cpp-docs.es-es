---
title: "Creating Pop-up Menus | Microsoft Docs"
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
  - "context menus, Menu Editor"
  - "pop-up menus, creating"
  - "menus, pop-up"
  - "menus, creating"
  - "shortcut menus, creating"
  - "pop-up menus, displaying"
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating Pop-up Menus
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los [menús emergentes](../mfc/menus-mfc.md) muestran comandos de pantalla que se utilizan con frecuencia. Pueden ser contextuales con respecto a la ubicación del puntero. Utilizar menús emergentes en la aplicación requiere compilar el menú y, a continuación, conectarlo al código de la aplicación.  
  
 Una vez creado el recurso de menú, el código de la aplicación debe cargar el recurso y usar [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) para que aparezca el menú. Cuando el usuario descarte el menú emergente al hacer clic fuera de él o en un comando, se devolverá esa función. Si el usuario elige un comando, se enviará el mensaje de ese comando a la ventana cuyo controlador se ha pasado.  
  
### Para crear un menú emergente  
  
1.  [Cree un menú](../windows/creating-a-menu.md) con un título vacío \(no proporcione ningún **Título**\).  
  
2.  [Agregue un comando de menú al menú nuevo](../Topic/Adding%20Commands%20to%20a%20Menu.md). Desplácese al primer comando de menú, bajo el título de menú en blanco \(el título provisional dice Escriba aquí\). Escriba un **Título** y cualquier otra información.  
  
     Repita este proceso para los demás comandos de menú del menú emergente.  
  
3.  Guarde el recurso de menú.  
  
    > [!TIP]
    >  Para obtener más información acerca de cómo ver el menú emergente, consulte [Ver un menú como menú emergente](../windows/viewing-a-menu-as-a-pop-up-menu.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Connecting a Pop\-up Menu to Your Application](../Topic/Connecting%20a%20Pop-up%20Menu%20to%20Your%20Application.md)   
 [Menu Editor](../mfc/menu-editor.md)