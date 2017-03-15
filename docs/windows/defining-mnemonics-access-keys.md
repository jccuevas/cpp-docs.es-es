---
title: "Defining Mnemonics (Access Keys) | Microsoft Docs"
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
  - "access keys [C++], adding"
  - "keyboard shortcuts [C++], controls"
  - "dialog box controls, mnemonics"
  - "access keys [C++], checking"
  - "mnemonics, checking for duplicate"
  - "mnemonics"
  - "mnemonics, dialog box controls"
  - "keyboard shortcuts [C++], uniqueness checking"
  - "Check Mnemonics command"
  - "controls [C++], access keys"
  - "access keys [C++]"
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Defining Mnemonics (Access Keys)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Normalmente, los usuarios del teclado desplazan el foco de entrada de un control a otro en el cuadro de diálogo con las teclas TAB y de dirección.  No obstante, puede definirse una tecla de acceso \(un nombre mnemotécnico o más fácil de recordar\) que permita a los usuarios elegir un control presionando una sola tecla.  
  
### Para definir una tecla de acceso para un control con una leyenda visible \(botones de comando, casillas y botones de radio\)  
  
1.  Seleccione el control en el cuadro de diálogo.  
  
2.  En la [ventana Propiedades](../Topic/Properties%20Window.md), en la propiedad **Caption**, escriba un nombre nuevo para el control, con el carácter **&** delante de la letra que desee establecer como tecla de acceso.  Por ejemplo, `&Radio1`.  
  
3.  Presione **Entrar**.  
  
     La tecla de acceso aparecerá subrayada en la leyenda, por ejemplo, **R**adio1.  
  
### Para definir una tecla de acceso para un control sin una leyenda visible  
  
1.  Cree una leyenda para el control usando un control **Static Text** del [cuadro de herramientas](../Topic/Toolbox.md).  
  
2.  En la leyenda de texto estático, incluya un símbolo **&** delante de la letra que desee designar como tecla de acceso.  
  
3.  Asegúrese de que el control de texto estático preceda inmediatamente al control correspondiente en el orden de tabulación.  
  
 Todas las teclas de acceso de un cuadro de diálogo deberán ser únicas.  
  
#### Para comprobar la existencia de teclas de acceso duplicadas  
  
1.  En el menú **Formato**, haga clic en **Comprobar teclas de acceso**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)