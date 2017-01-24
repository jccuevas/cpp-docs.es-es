---
title: "Switching Between Dialog Box Controls and Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "events [C++], viewing for controls"
  - "Windows messages [C++], controls"
  - "messages [C++], viewing for dialog boxes"
  - "Dialog editor, accessing code"
  - "code [C++], switching from Dialog Editor"
  - "controls [C++], jumping to code"
  - "Dialog editor, switching between controls and code"
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Switching Between Dialog Box Controls and Code
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En las aplicaciones MFC puede hacerse doble clic en los controles del cuadro de diálogo para saltar al código de su controlador o para crear con rapidez funciones auxiliares.  
  
 Cuando está seleccionado un control, con hacer clic en el botón **Eventos de control** o **Mensajes** de la [ventana Propiedades](../Topic/Properties%20Window.md) se puede ver una lista completa de los mensajes y eventos de Windows disponibles para el elemento seleccionado.  La elección de un elemento de la lista permite crear o editar funciones controladoras.  
  
### Para saltar al código desde el editor de cuadros de diálogo  
  
1.  Haga doble clic en un control del cuadro de diálogo para saltar a la declaración de su función controladora de mensajes más recientemente implementada.  \(En los cuadros de diálogo basados en ATL, siempre se salta a la definición del constructor\).  
  
### Para ver los eventos de un control  
  
1.  Seleccione el control y haga clic en el botón **Eventos de control** de la [ventana Propiedades](../Topic/Properties%20Window.md).  
  
    > [!NOTE]
    >  Si se hace clic en el botón **Eventos de control** con el focoen la *cuadro de diálogo*, se mostrará una lista de todos los controles del cuadro; esta lista puede expandirse para así poder editar los eventos de cada uno de los controles.  
  
     Cuando el foco esté en un control particular del cuadro de diálogo, podrá hacer clic en él con el botón secundario y seleccionar **Agregar controlador de eventos** en el menú contextual.  y, así, especificar la clase a la que se agrega el controlador.  Para obtener más información, vea [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).  
  
### Para ver los mensajes de un cuadro de diálogo  
  
1.  Seleccione el cuadro de diálogo y haga clic en el botón **Mensajes** de la [ventana Propiedades](../Topic/Properties%20Window.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Dialog Editor](../mfc/dialog-editor.md)