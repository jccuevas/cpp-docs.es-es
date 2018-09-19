---
title: Agregar controladores de eventos para controles de cuadro de diálogo (C++) | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], adding event handlers to controls
- controls [C++], event handlers
- dialog box controls [C++], events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5caec6d9d77d743fa1a8455819b813364bde27d0
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317061"
---
# <a name="adding-event-handlers-for-dialog-box-controls-c"></a>Agregar controladores de eventos para controles de cuadro de diálogo (C++)

Para los cuadros de diálogo de proyecto que ya están asociados con una clase, se puede aprovechar algunos accesos directos al crear controladores de eventos. Puede crear rápidamente un controlador para el evento de notificación de control predeterminado o para cualquier mensaje de Windows aplicable.

### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Para crear un controlador para el evento de notificación de control predeterminado

1. Haga doble clic en el control. El **texto** abre el editor.

2. Agregar código de controlador de notificación de control en el **texto** editor.

### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Para crear un controlador para cualquier mensaje de Windows aplicable

1. Haga clic en el control que desea controlar el evento de notificación.

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), haga clic en el **eventos de control** botón para mostrar la lista de eventos comunes de Windows asociado al control. Por ejemplo, el estándar **Aceptar** situado en la **sobre** cuadro de diálogo muestra los siguientes eventos de notificación:

   - BN_CLICKED

   - BN_DOUBLECLICKED

   - BN_KILLFOCUS

   - BN_SETFOCUS

   > [!NOTE]
   > Como alternativa, seleccione el cuadro de diálogo y haga clic en el **eventos de control** botón para mostrar la lista de eventos comunes de Windows para todos los controles en el cuadro de diálogo.

3. En el **propiedades** , haga clic en la columna derecha junto al evento para controlar y, a continuación, seleccione el nombre de evento de notificación sugerido (por ejemplo, `OnBnClickedOK` controla BN_CLICKED).

   > [!NOTE]
   > Como alternativa, puede proporcionar un nombre de controlador de eventos de su elección, en lugar de seleccionar el nombre del controlador de eventos predeterminado.

   Una vez haya seleccionado el evento, Visual Studio abre el **Editor de texto** y muestra el código del controlador de eventos. Por ejemplo, se agrega el código siguiente para el valor predeterminado `OnBnClickedOK`:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

Si desea agregar el controlador de eventos a una clase que no sea lo implementa el cuadro de diálogo, use el [Asistente de controlador de eventos](../ide/event-handler-wizard.md). Para obtener más información, consulte [agregando un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Eventos predeterminados de los controles](../windows/default-control-events.md)  
[Definición de variables miembro para controles de cuadro de diálogo](../windows/defining-member-variables-for-dialog-controls.md)  
[Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)  
[Agregar una clase](../ide/adding-a-class-visual-cpp.md)  
[Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)  
[Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)  
[Reemplazar una función Virtual](../ide/overriding-a-virtual-function-visual-cpp.md)  
[Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)  