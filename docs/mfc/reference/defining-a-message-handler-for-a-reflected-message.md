---
title: Definir un controlador de mensajes para un mensaje reflejado
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 89cb1631be7b8588d02518eacbc93b466a275828
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531881"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definir un controlador de mensajes para un mensaje reflejado

Una vez haya creado una nueva clase de control MFC, puede definir controladores de mensajes para él. Controladores de mensajes reflejados permiten la clase del control controlar sus propios mensajes antes de que se reciba el mensaje por el elemento primario. Puede usar la MFC [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) función para enviar mensajes desde el control a una ventana primaria.

Con esta funcionalidad, por ejemplo, es posible crear un cuadro de lista que actualizarse a sí mismo, en lugar de confiar en la ventana primaria que es así (dibujado por el propietario). Para obtener más información sobre los mensajes reflejados, vea [controlar mensajes reflejados](../../mfc/handling-reflected-messages.md).

Para crear un [control ActiveX](../../mfc/activex-controls-on-the-internet.md) con la misma funcionalidad, debe crear un proyecto para el control ActiveX.

> [!NOTE]
>  No se puede agregar un mensaje reflejado (OCM_*mensaje*) para un control ActiveX control mediante la ventana Propiedades, como se describe a continuación. Estos mensajes se deben agregar manualmente.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Para definir un controlador de mensajes para un mensaje reflejado desde la ventana Propiedades

1. Agregue un control, como una lista, un control rebar, una barra de herramientas o un control de árbol a un proyecto MFC.

1. En la vista de clases, haga clic en el nombre de la clase del control.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), el nombre de clase del control aparece en el **nombre de la clase** lista.

1. Haga clic en el **mensajes** botón para mostrar los mensajes de Windows disponibles para agregar al control.

1. Desplácese hacia abajo en la lista de mensajes en la ventana Propiedades hasta que vea el encabezado **reflejado**. Como alternativa, haga clic en el **categorías** botón y contraer la vista para ver el **reflejado** encabezado.

1. Seleccione el mensaje reflejado para el que desea definir un controlador. Mensajes reflejados se marcan con un signo igual (=).

1. Haga clic en la celda en la columna derecha en la ventana Propiedades para mostrar el nombre sugerido del controlador como \<Agregar >*HandlerName*. (Por ejemplo, el **= WM_CTLCOLOR** sugiere el controlador de mensajes \<Agregar >**CtlColor**).

1. Haga clic en el nombre sugerido para Aceptar. El controlador se agrega al proyecto.

   Los nombres de controlador de mensaje que se han agregado aparecen en la columna derecha de la ventana de mensajes reflejados.

9. Para editar o eliminar un controlador de mensajes, repita los pasos del 4 al 7. Haga clic en la celda que contiene el nombre del controlador para editar o eliminar y haga clic en la tarea apropiada.

## <a name="see-also"></a>Vea también

[Asignación de mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
