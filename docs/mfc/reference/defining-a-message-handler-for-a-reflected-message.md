---
title: Definir un controlador de mensajes para un mensaje reflejado
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907942"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definir un controlador de mensajes para un mensaje reflejado

Una vez creada una nueva clase de control MFC, puede definir controladores de mensajes para ella. Los controladores de mensajes reflejados permiten que la clase del control Controle sus propios mensajes antes de que el elemento primario reciba el mensaje. Puede usar la función [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) de MFC para enviar mensajes desde el control a una ventana primaria.

Con esta funcionalidad podría, por ejemplo, crear un cuadro de lista que se volverá a dibujar en lugar de depender de la ventana primaria para hacerlo (dibujado por el propietario). Para obtener más información sobre los mensajes reflejados, vea [controlar mensajes reflejados](../../mfc/handling-reflected-messages.md).

Para crear un [control ActiveX](../../mfc/activex-controls-on-the-internet.md) con la misma funcionalidad, debe crear un proyecto para el control ActiveX.

> [!NOTE]
>  No se puede Agregar un mensaje reflejado *(OCM_)* para un control ActiveX mediante el Asistente para clases, tal como se describe a continuación. Debe agregar estos mensajes manualmente.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Para definir un controlador de mensajes para un mensaje reflejado desde el Asistente para clases

1. Agregue un control, como una lista, un control rebar, una barra de herramientas o un control de árbol, a su proyecto MFC.

1. En Vista de clases, haga clic en el nombre de la clase de control.

1. En el [Asistente para clases](mfc-class-wizard.md), el nombre de clase del control aparece en la lista **nombre de clase** .

1. Haga clic en la pestaña **mensajes** para mostrar los mensajes de Windows disponibles para agregar al control.

1. Seleccione el mensaje reflejado para el que desea definir un controlador. Los mensajes reflejados se marcan con un signo igual (=).

1. Haga clic en la celda de la columna derecha en el Asistente para clases para mostrar el nombre sugerido del \<controlador como Add >*HandlerName*. (Por ejemplo, el controlador de mensajes de **= WM_CTLCOLOR** sugiere \<agregar >**CTLCOLOR**).

1. Haga clic en el nombre sugerido para aceptar. El controlador se agrega al proyecto.

1. Para editar o eliminar un controlador de mensajes, repita los pasos del 4 al 7. Haga clic en la celda que contiene el nombre del controlador que se va a editar o eliminar y haga clic en la tarea adecuada.

## <a name="see-also"></a>Vea también

[Asignación de mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigate-code-cpp.md)
