---
title: 'Windows Sockets: Notificaciones de Socket'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 10dbe6c0e1f486257c50efc4acf917cd9d596630
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167776"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Notificaciones de Socket

En este artículo se describen las funciones de notificación de las clases de socket. Estas funciones miembro son funciones de devolución de llamada que el marco llama para notificar a su objeto de socket los eventos importantes. Las funciones de notificación son:

- [Alreceive](../mfc/reference/casyncsocket-class.md#onreceive): notifica a este socket que hay datos en el búfer para que los recupere mediante una llamada a [Receive](../mfc/reference/casyncsocket-class.md#receive).

- [Alsend](../mfc/reference/casyncsocket-class.md#onsend): notifica a este socket que ahora puede enviar datos llamando a [send](../mfc/reference/casyncsocket-class.md#send).

- [Alaccept](../mfc/reference/casyncsocket-class.md#onaccept): notifica a este socket de escucha que puede aceptar solicitudes de conexión pendientes llamando a [Accept](../mfc/reference/casyncsocket-class.md#accept).

- [Alconnect](../mfc/reference/casyncsocket-class.md#onconnect): notifica a este socket de conexión que se ha completado su intento de conexión: quizás correctamente o quizás por error.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): notifica a este socket que el socket al que está conectado se ha cerrado.

    > [!NOTE]
    >  Una función de notificación adicional es [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Esta notificación indica al socket de recepción que el socket de envío tiene datos "fuera de banda" que se van a enviar. Los datos fuera de banda son un canal lógicamente independiente asociado a cada par de sockets de secuencias conectados. El canal fuera de banda se usa normalmente para enviar datos "urgentes". MFC admite datos fuera de banda. Los usuarios avanzados que trabajan con la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) podrían necesitar usar el canal fuera de banda, pero no se recomienda que los usuarios de la clase [CSocket](../mfc/reference/csocket-class.md) lo utilicen. La forma más sencilla consiste en crear un segundo socket para pasar estos datos. Para obtener más información acerca de los datos fuera de banda, vea la especificación de Windows Sockets, disponible en el Windows SDK.

Si deriva de la clase `CAsyncSocket`, debe invalidar las funciones de notificación para los eventos de red de interés para la aplicación. Si deriva una clase de la clase `CSocket`, es su elección si desea invalidar las funciones de notificación de interés. También puede usar `CSocket`, en cuyo caso las funciones de notificación tienen como valor predeterminado no hacer nada.

Estas funciones son funciones de devolución de llamada que se pueden reemplazar. `CAsyncSocket` y `CSocket` convertir mensajes en notificaciones, pero debe implementar el modo en que las funciones de notificación responden si desea usarlas. Se llama a las funciones de notificación en el momento en que el socket recibe una notificación de un evento de interés, como la presencia de datos que se van a leer.

MFC llama a las funciones de notificación para permitirle personalizar el comportamiento del socket en el momento en que se le notifica. Por ejemplo, podría llamar a `Receive` desde la función de notificación de `OnReceive`, es decir, cuando se le notifique que hay datos que leer, llame a `Receive` para leerlo. Este enfoque no es necesario, pero es un escenario válido. Como alternativa, puede usar la función de notificación para realizar el seguimiento del progreso, imprimir los mensajes de **seguimiento** , etc.

Puede aprovechar estas notificaciones invalidando las funciones de notificación en una clase de socket derivada y proporcionando una implementación.

Durante una operación como la recepción o el envío de datos, una `CSocket` objeto se vuelve sincrónicamente. Durante el estado sincrónico, las notificaciones destinadas a otros Sockets se ponen en cola mientras el socket actual espera la notificación que desea. (Por ejemplo, durante una llamada `Receive`, el socket desea que se lea una notificación). Una vez que el socket completa su operación sincrónica y vuelve a ser asincrónico, otros Sockets pueden empezar a recibir las notificaciones en cola.

> [!NOTE]
> En `CSocket`, nunca se llama a la función de notificación de `OnConnect`. En el caso de las conexiones, se llama a `Connect`, que devolverá cuando se complete la conexión (ya sea correctamente o con errores). Cómo se controlan las notificaciones de conexión es un detalle de la implementación de MFC.

Para obtener más información sobre cada función de notificación, vea la función en la `CAsyncSocket` de clase en la *referencia de MFC*. Para obtener código fuente e información sobre los ejemplos de MFC, vea [ejemplos de MFC](../overview/visual-cpp-samples.md#mfc-samples).

Para más información, consulte:

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Derivar de las clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
