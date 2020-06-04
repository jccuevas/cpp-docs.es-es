---
title: Agregar un controlador de eventos
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 0d852991c29281a7ecf912bd3d764d9916ef10f7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447510"
---
# <a name="add-an-event-handler"></a>Agregar un controlador de eventos

Desde el editor de recursos, se puede agregar un controlador de eventos nuevo o modificar uno existente para un control de cuadro de diálogo mediante el [Asistente para controladores de eventos](#event-handler-wizard).

Puede agregar un evento a la clase que implementa el cuadro de diálogo mediante la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Para agregar el evento a una clase que no sea la del cuadro de diálogo, use al Asistente para controladores de eventos.

**Para agregar un controlador de eventos a un control de cuadro de diálogo:**

1. Haga doble clic en el recurso de cuadro de diálogo en la [Vista de recursos](../windows/how-to-create-a-resource-script-file.md#create-resources) para abrir el recurso de cuadro de diálogo que contiene el control en el [Editor de cuadros de diálogo](../windows/dialog-editor.md).

1. Haga clic con el botón derecho en el control para el que quiera controlar el evento de notificación.

1. En el menú contextual, elija **Agregar controlador de eventos** para mostrar el Asistente para controladores de eventos.

1. Seleccione el evento en el cuadro **Tipo de mensaje** para agregar a la clase seleccionada en el cuadro **Lista de clases**.

1. Acepte el nombre predeterminado en el cuadro **Nombre del controlador de función** o proporcione uno de su elección.

1. Seleccione **Agregar y editar** para agregar el controlador de eventos al proyecto y abrir el editor de texto en la función nueva para agregar el código del controlador de eventos apropiado.

   Si el tipo de mensaje seleccionado ya tiene un controlador de eventos para la clase seleccionada, **Agregar y editar** no estará disponible, y **Editar código** sí. Seleccione **Editar código** para abrir el editor de texto en la función existente.

Como alternativa, puede agregar controladores de eventos desde la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Para obtener más información, vea [Agregar controladores de eventos para controles de cuadro de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md).

## <a name="in-this-section"></a>En esta sección

- [Asistente para controladores de eventos](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Asistente para controladores de eventos

Este asistente agrega un controlador de eventos para un control de cuadro de diálogo a la clase que elija. Si agrega un controlador de eventos desde la [ventana Propiedades](/visualstudio/ide/reference/properties-window), solo lo puede agregar a la clase que implementa el cuadro de diálogo. Para obtener más información, vea [Agregar controladores de eventos para controles de cuadro de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Nombre de comando**

  Identifica el control seleccionado, para el que se agrega el controlador de eventos. Este cuadro no está disponible.

- **Tipo de mensaje**

  Muestra la lista de controladores de mensajes posibles actuales para el control seleccionado.

- **Nombre del controlador de función**

  Muestra el nombre de la función agregada para controlar el evento. De forma predeterminada, el nombre se basa en el tipo de mensaje y el comando, precedido por `On`. Por ejemplo, para el botón denominado `IDC_BUTTON1`, el tipo de mensaje `BN_CLICKED` muestra el nombre del controlador de función `OnBnClickedButton1`.

- **Lista de clases**

  Muestra las clases disponibles a las que se puede agregar un controlador de eventos. La clase para el cuadro de diálogo seleccionado se muestra en color rojo.

- **Descripción del controlador**

  Proporciona una descripción para el elemento seleccionado en el cuadro **Tipo de mensaje**. Este cuadro no está disponible.

- **Agregar y editar**

  Agrega el controlador de mensajes al objeto o la clase seleccionados. Además, abre el editor de texto por la función nueva para que pueda agregar el código del controlador para la notificación del control.

- **Editar código**

  Abre el editor de texto por la función existente seleccionada para que pueda agregar o editar el código del controlador de notificación del control.
