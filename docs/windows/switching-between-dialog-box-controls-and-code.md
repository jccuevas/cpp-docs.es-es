---
title: Cambiar entre los controles de cuadro de diálogo y el código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog editor, accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog editor, switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ffcb4621bf0005e6b22991da7a2dde9372afa6c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891927"
---
# <a name="switching-between-dialog-box-controls-and-code"></a>Cambiar de los controles de un cuadro de diálogo al código
En las aplicaciones MFC, puede hacer doble clic en los controles de cuadro de diálogo para saltar a su código de controlador o para crear rápidamente código auxiliar funciones del controlador.  
  
 Con un control seleccionado, haga clic en el **eventos de control** botón o **mensajes** botón en el [ventana propiedades](/visualstudio/ide/reference/properties-window) para ver una lista completa de eventos y mensajes de Windows está disponible para el elemento seleccionado. Elija en la lista para crear o editar funciones del controlador.  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>Para saltar al código desde el editor de cuadro de diálogo  
  
1.  Haga doble clic en un control en el cuadro de diálogo para saltar a la declaración de su función de tratamiento de mensajes más recientemente implementada. (Para las clases de cuadro de diálogo basados en ATL, siempre se salta a la definición del constructor.)  
  
### <a name="to-view-events-for-a-control"></a>Para ver los eventos para un control  
  
1.  Con un control seleccionado, haga clic en el **eventos de control** botón en el [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
    > [!NOTE]
    >  Al hacer clic en el **eventos de control** botón cuando el *cuadro de diálogo* tiene foco expone una lista de todos los controles en el cuadro de diálogo, que, a continuación, se puede expandir para editar los eventos para los controles individuales.  
  
     Cuando un control único tiene el foco en el cuadro de diálogo, puede haga clic en él y seleccione **Agregar controlador de eventos** en el menú contextual. Esto le permite especificar la clase a la que se agrega el controlador. Para obtener más información, consulte [agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).  
  
### <a name="to-view-messages-for-a-dialog-box"></a>Para ver los mensajes de un cuadro de diálogo  
  
1.  Con el cuadro de diálogo seleccionado, haga clic en el **mensajes** botón en el [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de cuadros de diálogo](../windows/dialog-editor.md)

