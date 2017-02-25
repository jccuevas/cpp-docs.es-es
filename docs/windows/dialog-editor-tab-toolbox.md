---
title: "Editor de cuadros de di&#225;logo (Ficha, Cuadro de herramientas) | Microsoft Docs"
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
  - "Cuadro de herramientas [C++], pestaña Editor de cuadros de diálogo"
  - "controles [C++], tipos"
  - "controles syslink en cuadros de diálogo"
  - "controles personalizados [Visual Studio], cuadros de diálogo"
  - "controles [C++], estándar"
  - "Editor de cuadros de diálogo, crear controles"
  - "controles [C++], agregar a cuadros de diálogo"
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Editor de cuadros de di&#225;logo (Ficha, Cuadro de herramientas)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La pestaña Editor de cuadros de diálogo aparece en la [ventana del cuadro de herramientas](../Topic/Toolbox.md) cuando trabaja en el editor de cuadros de diálogo. Para agregar controles a su nuevo cuadro de diálogo, arrastre controles desde el cuadro de herramientas al cuadro de diálogo que está creando \(para más información, vea [Agregar un control a un cuadro de diálogo](../mfc/adding-a-control-to-a-dialog-box.md)\). Después, puede mover los controles o cambiar su tamaño y su forma.  
  
 Los controles estándares disponibles en el cuadro de herramientas son:  
  
-   [Button \(control\)](../mfc/reference/cbutton-class.md)  
  
-   [Check Box \(control\)](../mfc/reference/button-styles.md)  
  
-   [Combo Box \(control\)](../mfc/reference/ccombobox-class.md)  
  
-   [Edit \(control\)](../mfc/reference/cedit-class.md)  
  
-   Cuadro de grupo  
  
-   [List Box \(control\)](../mfc/reference/clistbox-class.md)  
  
-   [Radio Button \(control\)](../mfc/reference/button-styles.md)  
  
-   [Static Text \(control\)](../mfc/reference/cstatic-class.md)  
  
-   [Picture \(control\)](../mfc/reference/cpictureholder-class.md)  
  
-   [Rich Edit 2.0 \(control\)](../mfc/using-cricheditctrl.md)  
  
-   [Scroll Bar \(control\)](../mfc/reference/cscrollbar-class.md)  
  
 Los [controles comunes de Windows](../mfc/controls-mfc.md) disponibles en el cuadro de herramientas ofrecen una mayor funcionalidad en su aplicación. Son los siguientes:  
  
-   [Control deslizante](../mfc/slider-control-styles.md)  
  
-   [Control de botón de número](../mfc/using-cspinbuttonctrl.md)  
  
-   [Control de progreso](../mfc/styles-for-the-progress-control.md)  
  
-   [Hot Key \(control\)](../mfc/using-a-hot-key-control.md)  
  
-   [List \(control\)](../mfc/list-control-and-list-view.md)  
  
-   [Tree \(control\)](../mfc/tree-control-styles.md)  
  
-   [Control Tab](../mfc/tab-controls-and-property-sheets.md)  
  
-   [Animation \(control\)](../mfc/using-an-animation-control.md)  
  
-   [Date Time Picker \(control\)](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [Month Calendar \(control\)](../mfc/month-calendar-control-examples.md)  
  
-   [IP Address \(control\)](../mfc/reference/cipaddressctrl-class.md)  
  
-   [Extended Combo Box \(control\)](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [Custom \(control\)](../mfc/custom-controls-in-the-dialog-editor.md)  
  
 Para agregar controles personalizados al cuadro de diálogo, seleccione el **Control personalizado** en el cuadro de herramientas y arrástrelo al cuadro de diálogo. Para agregar un control Syslink, agregue un control personalizado y luego cambie la propiedad **Clase** del control a **Syslink**. Esto hará que se actualicen las propiedades y que muestren las propiedades del control Syslink. Para información sobre la clase contenedora de MFC, vea [CLinkCtrl](../mfc/reference/clinkctrl-class.md).  
  
 También puede [agregar controles ActiveX a su cuadro de diálogo](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 También puede personalizar la ventana del cuadro de herramientas para facilitar su uso. Para más información, vea [Administración de elementos y pestañas en el cuadro de herramientas](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db). Por ejemplo, puede colocar controles en la ventana del cuadro de herramientas para facilitar el acceso. Para más información, vea [Personalizar el cuadro de diálogo Cuadro de herramientas](http://msdn.microsoft.com/es-es/bd07835f-18a8-433e-bccc-7141f65263bb).  
  
 Para más información sobre el uso del control RichEdit 1.0 con MFC, vea [Utilizar el control RichEdit 1.0 con MFC](../mfc/using-the-richedit-1-0-control-with-mfc.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Controles](../mfc/controls-mfc.md)   
 [Clases de control](../mfc/control-classes.md)   
 [Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)   
 [Estilos de barra de desplazamiento](../mfc/reference/scroll-bar-styles.md)   
 [Ejemplos de control Rich Edit](../mfc/rich-edit-control-examples.md)   
 [Adding Event Handlers for Dialog Box Controls](../mfc/adding-event-handlers-for-dialog-box-controls.md)   
 [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)