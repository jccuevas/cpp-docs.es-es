---
title: "Agregar controladores de eventos para controles de cuadros de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Dialog editor, adding event handlers to controls
- controls [C++], event handlers
- dialog box controls, events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afe50d56d6b96cc4bc0b871f72c27feb0a750e89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-event-handlers-for-dialog-box-controls"></a>Agregar controladores de eventos para controles de cuadros de diálogo
Para cuadros de diálogo de proyecto que ya están asociadas a una clase, puede aprovechar las ventajas de algunos métodos abreviados al crear controladores de eventos. Puede crear rápidamente un controlador para el evento de notificación de control predeterminado o para cualquier mensaje de Windows aplicable.  
  
#### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Para crear un controlador para el evento de notificación de control predeterminado  
  
1.  Haga doble clic en el control. Se abrirá el editor de texto.  
  
2.  Agregar código de controlador de notificación de control en el editor de texto.  
  
#### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Para crear un controlador para cualquier mensaje de Windows aplicable  
  
1.  Haga clic en el control que desea controlar el evento de notificación.  
  
2.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), haga clic en el **eventos de control** botón para mostrar la lista de eventos comunes de Windows asociado al control. Por ejemplo, el estándar **Aceptar** situado en la **sobre** cuadro de diálogo muestra los siguientes eventos de notificación:  
  
 **BN_CLICKED**  
  
 **BN_DOUBLECLICKED**  
  
 **BN_KILLFOCUS**  
  
 **BN_SETFOCUS**  
  
    > [!NOTE]
    >  Como alternativa, seleccione el cuadro de diálogo y haga clic en el **eventos de control** botón para mostrar la lista de eventos comunes de Windows para todos los controles en el cuadro de diálogo.  
  
3.  En el **propiedades** ventana, haga clic en la columna derecha junto al evento para controlar y, a continuación, seleccione el nombre de evento de notificación sugerido (por ejemplo, **OnBnClickedOK** identificadores **BN_CLICKED** ).  
  
    > [!NOTE]
    >  Como alternativa, puede proporcionar un nombre de controlador de eventos de su elección, en lugar de seleccionar el nombre del controlador de eventos de forma predeterminada.  
  
     Una vez haya seleccionado el evento, Visual Studio abre el Editor de texto y muestra el código del controlador de eventos. Por ejemplo, se agrega el siguiente código para el valor predeterminado **OnBnClickedOK**:  
  
 ```  
    void CAboutDlg::OnBnClickedOk(void)  
 { *// TODO: Add your control notification handler code here  
 }  
 ```  
  
 Si desea agregar el controlador de eventos a una clase distinta de lo que se implementa el cuadro de diálogo, use la [Asistente de controlador de eventos](../ide/event-handler-wizard.md). Para obtener más información, consulte [agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Eventos de Control predeterminado](../windows/default-control-events.md)   
 [Definir Variables miembro para los controles de cuadro de diálogo](../windows/defining-member-variables-for-dialog-controls.md)   
 [Controles de cuadro de diálogo y tipos de Variable](../ide/dialog-box-controls-and-variable-types.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función Virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md)

