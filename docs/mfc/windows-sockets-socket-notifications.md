---
title: 'Windows Sockets: Notificaciones de Socket | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90dfddb72ba3362f0e6595ee4f34ea2145bb85ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375273"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Notificaciones de Socket

En este artículo se describe las funciones de notificación en las clases de socket. Estas funciones miembro son funciones de devolución de llamada que llama el marco de trabajo para notificar al objeto de socket de eventos importantes. Las funciones de notificación son:

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): notifica a este socket que hay datos en el búfer que puede recuperar mediante una llamada a [recepción](../mfc/reference/casyncsocket-class.md#receive).

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): notifica a este socket que ahora puede enviar datos mediante una llamada a [enviar](../mfc/reference/casyncsocket-class.md#send).

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): notifica a este socket de escucha que puede aceptar solicitudes de conexión pendientes llamando [Accept](../mfc/reference/casyncsocket-class.md#accept).

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): notifica a este socket de conexión que su intento de conexión completado: quizás correctamente o quizás en error.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): notifica a este socket que se ha cerrado el socket que está conectada.

    > [!NOTE]
    >  Es una función adicional de notificación [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Esta notificación indica al socket receptor que el socket remitente tiene datos de "fuera de banda" para enviar. Datos fuera de banda están un canal lógicamente independiente asociado a cada par de sockets de secuencias conectados. El canal fuera de banda normalmente se usa para enviar datos "urgentes". MFC admite datos fuera de banda. Trabajar con clases de usuarios avanzados [CAsyncSocket](../mfc/reference/casyncsocket-class.md) posible que deba utilizar el canal fuera de banda, pero los usuarios de la clase [CSocket](../mfc/reference/csocket-class.md) no se recomienda utilizarla. La manera más fácil es crear un segundo socket para transferir estos datos. Para obtener más información acerca de los datos fuera de banda, consulte la especificación Windows Sockets, disponible en el SDK de Windows.

Si deriva de la clase `CAsyncSocket`, debe invalidar las funciones de notificación para los eventos de interés para la aplicación de red. Si deriva una clase de la clase `CSocket`, es su opción si se debe invalidar las funciones de notificación de interés. También puede usar `CSocket` Sí, en cuyo caso la notificación de las funciones de forma predeterminada no hace nada.

Estas funciones son funciones de devolución de llamada que se puede invalidar. `CAsyncSocket` y `CSocket` convert mensajes para enviar notificaciones, pero debe implementar la notificación de funcionamiento de responder si desea usarlas. Se llama a las funciones de notificación en el momento en que se notifica al socket de un evento de interés, como la presencia de datos que deben leerse.

MFC llama a las funciones de notificación que le permiten personalizar el comportamiento del socket en el momento de la notificación. Por ejemplo, puede llamar a `Receive` desde su `OnReceive` función de notificación, es decir, en el que es una notificación que hay datos para leer, llamar a `Receive` para leerlo. Este enfoque no es necesario, pero es un escenario válido. Como alternativa, puede usar la función de notificación para seguir el progreso, imprimir **seguimiento** mensajes y así sucesivamente.

Puede aprovechar estas notificaciones reemplazando las funciones de notificación en una clase derivada de socket y proporcionar una implementación.

Durante una operación como la recepción o envío de datos, un `CSocket` objeto se convierte en sincrónica. Durante el estado sincrónico, las notificaciones para otros sockets se ponen en cola mientras espera la notificación que desea que el socket actual. (Por ejemplo, durante un `Receive` llamada, el socket desea leer una notificación.) Una vez que el socket complete la operación sincrónica y se convierte en asincrónico, otros sockets pueden empezar a recibir las notificaciones en cola.

> [!NOTE]
>  En `CSocket`, el `OnConnect` nunca se llama la función de notificación. Para las conexiones, se llama a `Connect`, que se devolverá cuando se complete la conexión (éxito o error). Cómo se controlan las notificaciones de conexión es un detalle de implementación de MFC.

Para obtener más información sobre cada función de notificación, vea la función de la clase `CAsyncSocket` en el *referencia de MFC*. Para código fuente e información acerca de los ejemplos MFC, vea [ejemplos de MFC](../visual-cpp-samples.md).

Para obtener más información, consulte:

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Derivar de las clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

