---
title: Procesar mensajes de notificación en un control Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 948990c8597c2ccdcec496252c6801c02a78cbf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507960"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Procesar mensajes de notificación en un control Rebar

En la clase primaria del control rebar, cree una `OnChildNotify` función de controlador con una instrucción switch para los mensajes de notificación de control rebar (`CReBarCtrl`) que desee controlar. Las notificaciones se envían a la ventana primaria cuando el usuario arrastra objetos sobre el control rebar, cambia el diseño de las bandas Rebar, elimina las bandas del control rebar, etc.

El objeto de control rebar puede enviar los siguientes mensajes de notificación:

- RBN_AUTOSIZE enviado por un control rebar (creado con el estilo RBS_AUTOSIZE) cuando el rebar cambia automáticamente de tamaño.

- RBN_BEGINDRAG enviado por un control Rebar cuando el usuario comienza a arrastrar una banda.

- RBN_CHILDSIZE enviado por un control Rebar cuando se cambia el tamaño de la ventana secundaria de una banda.

- RBN_DELETEDBAND enviado por un control rebar después de que se haya eliminado una banda.

- RBN_DELETINGBAND enviado por un control Rebar cuando una banda está a punto de eliminarse.

- RBN_ENDDRAG enviado por un control Rebar cuando el usuario deja de arrastrar una banda.

- RBN_GETOBJECT enviado por un control rebar (creado con el estilo RBS_REGISTERDROP) cuando se arrastra un objeto sobre una banda en el control.

- RBN_HEIGHTCHANGE enviado por un control Rebar cuando su alto ha cambiado.

- RBN_LAYOUTCHANGED enviado por un control Rebar cuando el usuario cambia el diseño de las bandas del control.

Para obtener más información sobre estas notificaciones, vea [referencia de control rebar](/windows/win32/controls/rebar-control-reference) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
