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
ms.openlocfilehash: 73315d4a1107204bc6adc885729fdeeaeb7f98d0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298979"
---
# <a name="receiving-notification-from-common-controls"></a>Recibir notificaciones de los controles comunes

Los controles comunes son ventanas secundarias que envían mensajes de notificación a la ventana primaria cuando se producen eventos, como la entrada del usuario, en el control.

La aplicación se basa en estos mensajes de notificación para determinar qué acción desea que realice el usuario. Los controles más comunes envían mensajes de notificación como mensajes de WM_NOTIFY. Los controles de Windows envían la mayoría de los mensajes de notificación como mensajes de WM_COMMAND. [CWnd:: alnotify](../mfc/reference/cwnd-class.md#onnotify) es el controlador del mensaje de WM_NOTIFY. Al igual que con `CWnd::OnCommand`, la implementación de `OnNotify` envía el mensaje de notificación a `OnCmdMsg` para el control de los mapas de mensajes. La entrada de mapa de mensajes para controlar las notificaciones es ON_NOTIFY. Para obtener más información, vea la [Nota técnica 61: ON_NOTIFY y WM_NOTIFY mensajes](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Como alternativa, una clase derivada puede controlar sus propios mensajes de notificación mediante "reflexión de mensajes". Para obtener más información, vea la [Nota técnica 62: reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Recuperar la posición del cursor en un mensaje de notificación

En ocasiones, resulta útil determinar la posición actual del cursor cuando un control común recibe determinados mensajes de notificación. Por ejemplo, sería útil determinar la ubicación actual del cursor cuando un control común recibe un mensaje de notificación de NM_RCLICK.

Hay una manera sencilla de lograrlo llamando a `CWnd::GetCurrentMessage`. Sin embargo, este método solo recupera la posición del cursor en el momento en que se envió el mensaje. Dado que es posible que el cursor se haya cambiado desde que se envió el mensaje, debe llamar a `CWnd::GetCursorPos` para obtener la posición actual del cursor.

> [!NOTE]
>  solo se debe llamar a `CWnd::GetCurrentMessage` dentro de un controlador de mensajes.

Agregue el código siguiente al cuerpo del controlador de mensajes de notificación (en este ejemplo, NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

En este punto, la ubicación del cursor del mouse se almacena en el objeto `cursorPos`.

## <a name="see-also"></a>Vea también

[Creación y uso de controles](../mfc/making-and-using-controls.md)<br/>
[Controles](../mfc/controls-mfc.md)
