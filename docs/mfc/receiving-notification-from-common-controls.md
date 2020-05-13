---
title: Recibir notificaciones de los controles comunes
ms.date: 11/04/2016
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
ms.openlocfilehash: 9205facb5ec4e2491308020d9667a27ab8deb96b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371782"
---
# <a name="receiving-notification-from-common-controls"></a>Recibir notificaciones de los controles comunes

Los controles comunes son ventanas secundarias que envían mensajes de notificación a la ventana primaria cuando se producen eventos, como la entrada del usuario, en el control.

La aplicación se basa en estos mensajes de notificación para determinar qué acción desea que realice el usuario. Los controles más comunes envían mensajes de notificación como mensajes WM_NOTIFY. Los controles de Windows envían la mayoría de los mensajes de notificación como mensajes WM_COMMAND. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) es el controlador del mensaje WM_NOTIFY. Al `CWnd::OnCommand`igual que `OnNotify` con , la `OnCmdMsg` implementación de distribuye el mensaje de notificación para su control en mapas de mensajes. La entrada de mapa de mensajes para controlar notificaciones es ON_NOTIFY. Para obtener más información, consulte [Nota técnica 61: mensajes de ON_NOTIFY y WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Como alternativa, una clase derivada puede controlar sus propios mensajes de notificación mediante "reflexión de mensajes." Para obtener más información, vea [Nota técnica 62: Reflexión](../mfc/tn062-message-reflection-for-windows-controls.md)de mensajes para controles de Windows .

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Recuperar la posición del cursor en un mensaje de notificación

En ocasiones, es útil determinar la posición actual del cursor cuando un control común recibe determinados mensajes de notificación. Por ejemplo, sería útil determinar la ubicación actual del cursor cuando un control común recibe un mensaje de notificación NM_RCLICK.

Hay una manera sencilla de `CWnd::GetCurrentMessage`lograr esto llamando a . Sin embargo, este método solo recupera la posición del cursor en el momento en que se envió el mensaje. Dado que el cursor puede haberse movido `CWnd::GetCursorPos` desde que se envió el mensaje, debe llamar para obtener la posición actual del cursor.

> [!NOTE]
> `CWnd::GetCurrentMessage`solo se debe llamar dentro de un controlador de mensajes.

Agregue el código siguiente al cuerpo del controlador de mensajes de notificación (en este ejemplo, NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

En este punto, la ubicación del `cursorPos` cursor del ratón se almacena en el objeto.

## <a name="see-also"></a>Consulte también

[Creación y uso de controles](../mfc/making-and-using-controls.md)<br/>
[Controles](../mfc/controls-mfc.md)
