---
title: Recibir notificaciones de controles comunes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30e89c8d25d78477ed98bae0fd06a704e32d3906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349718"
---
# <a name="receiving-notification-from-common-controls"></a>Recibir notificaciones de los controles comunes
Controles comunes son ventanas secundarias que envían mensajes de notificación a la ventana primaria cuando se producen eventos, como la entrada del usuario, en el control.  
  
 La aplicación se basa en estos mensajes de notificación para determinar qué acción desea que el usuario que tenga. Controles más comunes de envían mensajes de notificación como **WM_NOTIFY** mensajes. Controles de Windows envían la mayoría de mensajes de notificación como **WM_COMMAND** mensajes. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) es el controlador para el **WM_NOTIFY** mensaje. Al igual que con `CWnd::OnCommand`, la implementación de `OnNotify` envía el mensaje de notificación a `OnCmdMsg` para el control de mapas de mensajes. La entrada de mapa de mensajes para controlar notificaciones es `ON_NOTIFY`. Para obtener más información, consulte [Nota técnica 61: mensajes ON_NOTIFY y WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md).  
  
 Como alternativa, una clase derivada puede controlar sus propios mensajes de notificación mediante la "reflexión de mensajes". Para obtener más información, consulte [Nota técnica 62: reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Recuperar la posición del Cursor en un mensaje de notificación  
 En ocasiones, resulta útil para determinar la posición actual del cursor cuando se reciben ciertos mensajes de notificación por un control común. Por ejemplo, sería útil determinar la ubicación actual del cursor cuando un control común recibe un **NM_RCLICK** mensaje de notificación.  
  
 Hay una manera sencilla de lograrlo mediante una llamada a `CWnd::GetCurrentMessage`. Sin embargo, este método sólo recupera la posición del cursor en el momento en que se envió el mensaje. Dado que el cursor se haya movido desde que se envió el mensaje se debe llamar a **CWnd:: GetCursorPos** para obtener la posición actual del cursor.  
  
> [!NOTE]
>  `CWnd::GetCurrentMessage` solo debe llamarse en un controlador de mensajes.  
  
 Agregue el código siguiente al cuerpo del controlador de mensajes de notificación (en este ejemplo, **NM_RCLICK**):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]  
  
 En este momento, se almacena la ubicación del cursor del mouse en el `cursorPos` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Crear y utilizar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)

