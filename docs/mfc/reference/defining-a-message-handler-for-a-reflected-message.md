---
title: Definir un controlador de mensajes para un mensaje reflejado
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365854"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definir un controlador de mensajes para un mensaje reflejado

Una vez que haya creado una nueva clase de control MFC, puede definir controladores de mensajes para ella. Los controladores de mensajes reflejados permiten que la clase de control controle sus propios mensajes antes de que el elemento primario reciba el mensaje. Puede usar la función [MFC CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) para enviar mensajes desde el control a una ventana primaria.

Con esta funcionalidad, por ejemplo, podría crear un cuadro de lista que se redibujará a sí mismo en lugar de confiar en la ventana primaria para hacerlo (propietario dibujado). Para obtener más información sobre los mensajes reflejados, consulte Control de [mensajes reflejados](../../mfc/handling-reflected-messages.md).

Para crear un [control ActiveX](../../mfc/activex-controls-on-the-internet.md) con la misma funcionalidad, debe crear un proyecto para el control ActiveX.

> [!NOTE]
> No puede agregar un mensaje reflejado (OCM_*Message*) para un control ActiveX mediante el Asistente para clases, como se describe a continuación. Debe agregar estos mensajes manualmente.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Para definir un controlador de mensajes para un mensaje reflejado desde el Asistente para clases

1. Agregue un control, como una lista, un control de armadura, una barra de herramientas o un control de árbol, al proyecto MFC.

1. En la vista de clases, haga clic en el nombre de la clase de control.

1. En el [Asistente para clases](mfc-class-wizard.md), el nombre de clase de control aparece en la lista Nombre de **clase.**

1. Haga clic en la pestaña **Mensajes** para mostrar los mensajes de Windows disponibles para agregar al control.

1. Seleccione el mensaje reflejado para el que desea definir un controlador. Los mensajes reflejados se marcan con un signo igual (o).

1. Haga clic en la celda de la columna derecha del \<Asistente para clases para mostrar el nombre sugerido del controlador como agregar>*HandlerName*. (Por ejemplo, el controlador de \<mensajes de **WM_CTLCOLOR** sugiere agregar>**CtlColor**).

1. Haga clic en el nombre sugerido para aceptarlo. El controlador se agrega al proyecto.

1. Para editar o eliminar un controlador de mensajes, repita los pasos del 4 al 7. Haga clic en la celda que contiene el nombre del controlador para editar o eliminar y haga clic en la tarea adecuada.

## <a name="see-also"></a>Consulte también

[Asignación de mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navegar por la estructura de clases](../../ide/navigate-code-cpp.md)
