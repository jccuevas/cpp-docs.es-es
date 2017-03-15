---
title: "Grouping Radio Buttons on a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.grouping"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "member variables, adding to radio button groups"
  - "variables, dialog box control member variables"
  - "dialog box controls, grouping radio buttons"
  - "grouping controls"
  - "radio buttons, grouping on dialog boxes"
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Grouping Radio Buttons on a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al agregar botones de radio a un cuadro de diálogo, trátelos como grupo, estableciendo una propiedad Grupo en la ventana Propiedades para el primer botón del grupo. Después, aparecerá un id. de control para ese botón de opción en el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), lo que le permite agregar una variable miembro para el grupo de botones de radio.  
  
 Puede tener más de un grupo de botones de radio en un cuadro de diálogo y se debe agregar cada grupo mediante el siguiente procedimiento.  
  
### Para agregar un grupo de botones de radio a un cuadro de diálogo  
  
1.  Seleccione el control de botón de radio en la [ventana del cuadro de herramientas](../Topic/Toolbox.md) y haga clic en la ubicación del cuadro de diálogo donde quiere colocar el control.  
  
2.  Repita el paso 1 para agregar tantos botones de radio como necesite. Asegúrese de que los botones de radio del grupo sean consecutivos en el orden de tabulación \(para más información, vea [Cambiar el orden de tabulación de los controles](../mfc/changing-the-tab-order-of-controls.md)\).  
  
3.  En la [Ventana Propiedades](../Topic/Properties%20Window.md), establezca la propiedad **Grupo** del *primer* botón de radio en el orden de tabulación en **True**.  
  
     Al cambiar la propiedad **Grupo** a **True** se agrega el estilo WS\_GROUP a la entrada del botón en el objeto de diálogo del script de recursos y se asegura que un usuario solo puede seleccionar un botón de radio cada vez en el grupo de botones \(cuando el usuario hace clic en un botón de radio, se borran los demás miembros del grupo\).  
  
    > [!NOTE]
    >  Solo el primer botón de radio del grupo debe tener la propiedad **Grupo** establecida en **True**. Si dispone de otros controles que no forman parte del grupo de botones, establezca la propiedad **Grupo** del primer control *que se encuentra fuera del grupo* también en **True**. Para identificar rápidamente el primer control fuera del grupo, presione CTRL\+D para ver el orden de tabulación.  
  
### Para agregar una variable miembro para el grupo de botones de radio  
  
1.  Haga clic con el botón secundario en el primer control de botón de radio en el orden de tabulación \(el control dominante y el otro con la propiedad **Grupo** establecida en True\).  
  
2.  Elija **Agregar variable** en el menú contextual.  
  
3.  En el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), active la casilla **Variable de control** y luego seleccione el botón de radio **Valor**.  
  
4.  En el cuadro **Nombre de variable**, escriba un nombre para la nueva variable miembro.  
  
5.  En el cuadro de lista **Tipo de variable**, seleccione **int** o escriba **int**.  
  
6.  Ahora puede modificar el código para especificar qué botón de radio debe aparecer seleccionado. Por ejemplo,m\_radioBox1 \= 0 selecciona el primer botón de radio del grupo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)