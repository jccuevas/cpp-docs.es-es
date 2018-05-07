---
title: Agregar un controlador de eventos (Visual C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184161b22358f77845b5f7c4b6da0bb42f3ea15f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="adding-an-event-handler-visual-c"></a>Agregar un controlador de eventos (Visual C++)
En el editor de recursos, puede agregar un nuevo controlador de eventos o editar un controlador de eventos existente para un control de cuadro de diálogo mediante la [Asistente para controladores de eventos](../ide/event-handler-wizard.md).  
  
 Puede agregar un evento a la clase que implementa el cuadro de diálogo mediante la [ventana propiedades](/visualstudio/ide/reference/properties-window). Si desea agregar el evento a una clase distinta de la clase de cuadro de diálogo, utilice al Asistente para controladores de eventos.  
  
### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>Para agregar un controlador de eventos a un control de cuadro de diálogo  
  
1.  Haga doble clic en el recurso de cuadro de diálogo en [vista de recursos](../windows/resource-view-window.md) para abrir el recurso de cuadro de diálogo que contiene el control en el [editor de cuadro de diálogo](../windows/dialog-editor.md).  
  
2.  Haga clic en el control que desea controlar el evento de notificación.  
  
3.  En el menú contextual, haga clic en **Agregar controlador de eventos** para mostrar el Asistente para controladores de eventos.  
  
4.  Seleccione el evento en el **tipo de mensaje** para agregar a la clase seleccionada en el **lista de clases** cuadro.  
  
5.  Acepte el nombre predeterminado en el **nombre del controlador de función** cuadro o proporcionar el nombre de su elección.  
  
6.  Haga clic en **agregar y editar** para agregar el controlador de eventos al proyecto y abre el editor de texto en la nueva función para agregar el código del controlador de eventos apropiado.  
  
     Si el tipo de mensaje seleccionado ya tiene un controlador de eventos para la clase seleccionada, **agregar y editar** no está disponible, y **editar código** está disponible. Haga clic en **editar código** para abrir el editor de texto en la función existente.  
  
 Como alternativa, puede agregar controladores de eventos de la [ventana propiedades](/visualstudio/ide/reference/properties-window). Vea [agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)