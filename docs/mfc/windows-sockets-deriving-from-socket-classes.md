---
title: 'Windows Sockets: Derivar desde clases de Socket | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64fb9a3ff1c27aade9f74a8ed95a8016829874ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384080"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets: Derivar de las clases de socket
Este artículo describen algunas de las funciones que se obtiene al derivar su propia clase de una de las clases de socket.  
  
 Puede derivar sus propias clases de socket desde [CAsyncSocket](../mfc/reference/casyncsocket-class.md) o [CSocket](../mfc/reference/csocket-class.md) para agregar su propia funcionalidad. En concreto, estas clases proporcionan una serie de funciones de miembro virtual que se pueden reemplazar. Estas funciones se incluyen [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), y [OnClose](../mfc/reference/casyncsocket-class.md#onclose). Puede invalidar las funciones en la clase socket derivada para aprovechar las ventajas de las notificaciones que se proporcionan cuando se producen eventos de red. El marco de trabajo llama a estas funciones de devolución de llamada de notificación para recibir una notificación de eventos de socket importantes, como la recepción de datos que puede comenzar a leer. Para obtener más información acerca de las funciones de notificación, consulte [Windows Sockets: sockets de notificación](../mfc/windows-sockets-socket-notifications.md).  
  
 Además, la clase `CSocket` proporciona el [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) función miembro (avanzada reemplazable). MFC llama a esta función mientras el socket suministra mensajes basados en Windows. Puede invalidar `OnMessagePending` para buscar mensajes concretos de Windows y responder a ellos.  
  
 La versión predeterminada de `OnMessagePending` incluida en la clase `CSocket` examina la cola de mensajes para `WM_PAINT` mensajes mientras se espera a que se complete una llamada de bloqueo. Envía los mensajes de paint para mejorar la calidad de la pantalla. Además de hacer algo útil, ilustra una forma podrían invalidar la función usted mismo. Como otro ejemplo, considere el uso de `OnMessagePending` para la tarea siguiente. Supongamos que muestra un cuadro de diálogo no modal mientras se espera que se complete una transacción de red. El cuadro de diálogo contiene un botón de cancelación que el usuario puede utilizar para cancelar las transacciones de bloqueo que tardan demasiado tiempo. Su `OnMessagePending` invalidación podría suministrar mensajes relacionados con este cuadro de diálogo no modal.  
  
 En su `OnMessagePending` invalidar, devolver **TRUE** o el valor devuelto de una llamada a la versión de la clase base de `OnMessagePending`. Llamar a la versión de la clase base si realiza el trabajo que desea realizada.  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

