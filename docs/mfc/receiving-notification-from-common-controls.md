---
title: Recibir notificaciones de los controles comunes
ms.date: 11/04/2016
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
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
ms.openlocfilehash: 8813a7f86bde417b48d5ab2d943d296efef5e91c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542654"
---
# <a name="receiving-notification-from-common-controls"></a>Recibir notificaciones de los controles comunes

Controles comunes son ventanas secundarias que envían mensajes de notificación a la ventana primaria cuando se produzcan eventos, como la entrada del usuario, en el control.

La aplicación se basa en estos mensajes de notificación para determinar la acción que el usuario desea realizar. Los controles más comunes de envían mensajes de notificación como mensajes WM_NOTIFY. Controles de Windows envían la mayoría de los mensajes de notificación como mensajes WM_COMMAND. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) es el controlador para el mensaje WM_NOTIFY. Igual que con `CWnd::OnCommand`, la implementación de `OnNotify` envía el mensaje de notificación al `OnCmdMsg` para el control de mapas de mensajes. La entrada de mapa de mensajes para controlar las notificaciones es ON_NOTIFY. Para obtener más información, consulte [Nota técnica 61: mensajes ON_NOTIFY y Wm_notify](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Como alternativa, una clase derivada puede controlar sus propios mensajes de notificación mediante "reflexión de mensajes". Para obtener más información, consulte [Nota técnica 62: reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Recuperar la posición del Cursor en un mensaje de notificación

En ocasiones, es útil determinar la posición actual del cursor cuando se reciben ciertos mensajes de notificación mediante un control común. Por ejemplo, sería útil determinar la ubicación actual del cursor cuando un control común recibe un mensaje de notificación NM_RCLICK.

Hay una manera sencilla de lograrlo mediante una llamada a `CWnd::GetCurrentMessage`. Sin embargo, este método solo recupera la posición del cursor en el momento en que se envió el mensaje. Dado que el cursor es posible que se han movido desde que se envió el mensaje se debe llamar a `CWnd::GetCursorPos` para obtener la posición actual del cursor.

> [!NOTE]
>  `CWnd::GetCurrentMessage` solo debe llamarse dentro de un controlador de mensajes.

Agregue el código siguiente al cuerpo del controlador de mensajes de notificación (en este ejemplo, NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

En este momento, se almacena la ubicación del cursor del mouse en el `cursorPos` objeto.

## <a name="see-also"></a>Vea también

[Creación y uso de controles](../mfc/making-and-using-controls.md)<br/>
[Controles](../mfc/controls-mfc.md)

