---
title: "Adding Event Handlers for Dialog Box Controls | Microsoft Docs"
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
  - "Dialog editor, adding event handlers to controls"
  - "controls [C++], event handlers"
  - "dialog box controls, events"
  - "event handlers, for dialog box controls"
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Adding Event Handlers for Dialog Box Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En los cuadros de diálogo de proyectos que ya estén asociados a una clase, puede sacar partido de algunos accesos directos a la hora de crear controladores de eventos.  Es muy fácil crear un controlador para el evento predeterminado de notificación de control o para cualquier mensaje de Windows aplicable.  
  
#### Para crear un controlador para el evento de notificación de control predeterminado  
  
1.  Haga doble clic en el control.  Se abrirá el Editor de texto.  
  
2.  Agregue el código del controlador de notificación de control en el Editor de texto.  
  
#### Para crear un controlador para cualquier mensaje de Windows aplicable  
  
1.  Haga clic en el control cuyo evento de notificación desee controlar.  
  
2.  En la [ventana Propiedades](../Topic/Properties%20Window.md), haga clic en el botón **Eventos de control** para mostrar la lista de eventos comunes de Windows asociados al control.  Por ejemplo, el botón **Aceptar** estándar del cuadro de diálogo **Acerca de** muestra los siguientes eventos de notificación:  
  
     **BN\_CLICKED**  
  
     **BN\_DOUBLECLICKED**  
  
     **BN\_KILLFOCUS**  
  
     **BN\_SETFOCUS**  
  
    > [!NOTE]
    >  También puede seleccionar el cuadro de diálogo y hacer clic en el botón **Eventos de control** para que se muestre la lista de eventos comunes de Windows para todos los controles del cuadro de diálogo.  
  
3.  En la ventana **Propiedades**, haga clic en la columna derecha próxima al evento que desee controlar y seleccione el nombre de evento de notificación sugerido \(por ejemplo, **OnBnClickedOK** controla **BN\_CLICKED**\).  
  
    > [!NOTE]
    >  Otra posibilidad es proporcionar un nombre de controlador de eventos elegido por el usuario en lugar de seleccionar el nombre predeterminado.  
  
     Una vez seleccionado el evento, Visual Studio abre el Editor de texto y muestra el código del controlador del evento.  Por ejemplo, para **OnBnClickedOK** se agrega el siguiente código de forma predeterminada:  
  
    ```  
    void CAboutDlg::OnBnClickedOk(void)  
    {  
       // TODO: Add your control notification handler code here  
    }  
    ```  
  
 Si desea agregar el controlador de eventos a una clase distinta de la que implementa el cuadro de diálogo, use el [Asistente para controladores de eventos](../ide/event-handler-wizard.md).  Para obtener más información, vea [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 Win32  
  
## Vea también  
 [Default Control Events](../mfc/default-control-events.md)   
 [Defining Member Variables for Dialog Controls](../mfc/defining-member-variables-for-dialog-controls.md)   
 [Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)