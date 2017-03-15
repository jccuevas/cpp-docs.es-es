---
title: "Changing the Tab Order of Controls | Microsoft Docs"
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
  - "controls [C++], tab order"
  - "focus, tab order"
  - "tab controls, tab order"
  - "Tabstop property for controls"
  - "controls [C++], focus"
  - "dialog box controls, tab order"
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Changing the Tab Order of Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El orden de tabulación se refiere al orden en que la tecla TAB va desplazando el foco de entrada de un control al siguiente en un cuadro de diálogo.  Normalmente, el orden de tabulación en un cuadro de diálogo es de izquierda a derecha y de arriba a abajo.  Cada control tiene una propiedad **Tabstop** que determina si ha de recibir el foco de entrada.  
  
### Para establecer el foco en un control  
  
1.  En la [ventana Propiedades](../Topic/Properties%20Window.md), seleccione **True** o **False** en la propiedad **Tabstop**.  
  
 Incluso los controles que no tengan la propiedad Tabstop establecida en True deberán formar parte del orden de tabulación.  Esto puede ser importante, por ejemplo, cuando se [definen las teclas de acceso](../mfc/defining-mnemonics-access-keys.md) de controles sin leyenda.  El texto estático con la tecla de acceso asociada a un control deberá preceder inmediatamente al control en cuestión en el orden de tabulación.  
  
> [!NOTE]
>  Si un cuadro de diálogo contiene controles superpuestos, al cambiar el orden de tabulación puede que se altere el modo en que se muestren los controles.  Los últimos controles en el orden de tabulación se mostrarán siempre sobre cualquier control superpuesto que los preceda en el orden de tabulación.  
  
#### Para ver el orden de tabulación actual de todos los controles de un cuadro de diálogo  
  
1.  En el menú **Formato**, haga clic en **Orden de tabulación**.  
  
 \-O bien\-  
  
-   Presione CTRL \+ D.  
  
#### Para cambiar el orden de tabulación de todos los controles de un cuadro de diálogo  
  
1.  En el menú **Formato**, haga clic en **Orden de tabulación**.  
  
     Aparecerá un número en la esquina superior izquierda de cada control con el que se indicará su lugar en el orden de tabulación.  
  
2.  Defina el orden de tabulación haciendo clic en cada control según el orden que desee que siga la tecla TAB.  
  
3.  Presione **ENTRAR** para salir del modo **Orden de tabulación**.  
  
    > [!TIP]
    >  En el modo Orden de tabulación, si se presiona ESC o ENTRAR, se deshabilita la capacidad para cambiar el orden de tabulación.  
  
#### Para cambiar el orden de tabulación de dos o más controles  
  
1.  En el menú **Formato**, elija **Orden de tabulación**.  
  
2.  Especifique en qué punto ha de empezar el cambio en el orden.  Para ello, mantenga presionada la tecla **CTRL** y haga clic en el control anterior a aquél en el que desea que empiece a cambiar el orden.  
  
     Por ejemplo, si desea cambiar el orden de los controles 7 a 9, mantenga presionada CTRL y seleccione primero el control 6.  
  
    > [!NOTE]
    >  Para definir un control en particular con el número 1 \(el primero en el orden de tabulación\), haga doble clic sobre dicho control.  
  
3.  Suelte la tecla CTRL y vaya haciendo clic en los controles en el orden en que desee que siga la tecla TAB a partir de ese punto.  
  
4.  Presione **ENTRAR** para salir del modo **Orden de tabulación**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 Win32  
  
## Vea también  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)