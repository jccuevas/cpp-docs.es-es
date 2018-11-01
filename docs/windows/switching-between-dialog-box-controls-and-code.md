---
title: Cambiar entre código y los controles de cuadro de diálogo cuadro (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
ms.openlocfilehash: 4d48386e93fcea6d30fee6c57c288944bbd8d9ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644306"
---
# <a name="switching-between-dialog-box-c-controls-and-code"></a>Cambiar entre código y los controles de cuadro de diálogo cuadro (C++)

En las aplicaciones MFC, puede hacer doble clic en los controles de cuadro de diálogo para saltar al código de su controlador o para crear rápidamente código auxiliar de funciones del controlador.

Con un control seleccionado, haga clic en el **eventos de control** botón o la **mensajes** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window) para ver una lista completa de eventos y mensajes de Windows está disponible para el elemento seleccionado. Elija en la lista para crear o editar funciones de controlador.

### <a name="to-jump-to-code-from-the-dialog-editor"></a>Para saltar al código desde el editor de cuadro de diálogo

1. Haga doble clic en un control en el cuadro de diálogo para saltar a la declaración de su función de control de mensajes más recientemente implementada. (Para las clases de cuadro de diálogo basado en ATL, siempre se salta a la definición del constructor.)

### <a name="to-view-events-for-a-control"></a>Para ver los eventos de un control

1. Con un control seleccionado, haga clic en el **eventos de control** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window).

   > [!NOTE]
   > Al hacer clic en el **eventos de control** botón cuando el *cuadro de diálogo* tiene foco expone una lista de todos los controles en el cuadro de diálogo, que, a continuación, se puede expandir para modificar los eventos para los controles individuales.

   Cuando un solo control tiene el foco en el cuadro de diálogo, puede haga clic en él y seleccione **Add Event Handler** en el menú contextual. Esto le permite especificar la clase a la que se agrega el controlador. Para obtener más información, consulte [agregando un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).

### <a name="to-view-messages-for-a-dialog-box"></a>Para ver los mensajes para un cuadro de diálogo

1. Con el cuadro de diálogo seleccionado, haga clic en el **mensajes** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cuadros de diálogo](../windows/dialog-editor.md)