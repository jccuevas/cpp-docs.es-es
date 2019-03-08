---
title: Procesar mensajes de notificación en un control Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 8ac225802bd1d0a0a4b0f30e017fa677f1072fd3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296298"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Procesar mensajes de notificación en un control Rebar

En la clase primaria del control rebar, cree un `OnChildNotify` función de controlador con una instrucción switch para cualquier control rebar (`CReBarCtrl`) mensajes de notificación que desee controlar. Las notificaciones se envían a la ventana primaria cuando el usuario arrastra objetos sobre el control de rebar, cambia el diseño de las bandas rebar, elimina bandas del control rebar y así sucesivamente.

El objeto de control rebar pueden enviar los mensajes de notificación siguiente:

- RBN_AUTOSIZE se envía mediante un control rebar (creado con el estilo RBS_AUTOSIZE) cuando el control rebar cambia automáticamente de tamaño.

- RBN_BEGINDRAG se envía mediante un control rebar cuando el usuario comienza a arrastrar una banda.

- RBN_CHILDSIZE se envía mediante un control rebar cuando se cambia el tamaño de ventana secundaria de la de la banda.

- RBN_DELETEDBAND se envía mediante un control rebar después de que se ha eliminado una banda.

- RBN_DELETINGBAND se envía mediante un control rebar cuando una banda está a punto de eliminarse.

- RBN_BEGINDRAG se envía mediante un control rebar cuando el usuario deja de arrastrar una banda.

- RBN_GETOBJECT se envía mediante un control rebar (creado con el estilo RBS_REGISTERDROP) cuando se arrastra un objeto a través de una banda en el control.

- RBN_HEIGHTCHANGE se envía mediante un control rebar cuando ha cambiado su alto.

- RBN_LAYOUTCHANGED se envía mediante un control rebar cuando el usuario cambia el diseño de las bandas del control.

Para obtener más información sobre estas notificaciones, consulte [referencia del Control Rebar](/windows/desktop/controls/rebar-control-reference) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
