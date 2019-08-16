---
title: 'Windows Sockets: Bloqueo'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 26a361bc63da5f6e75144cc91fe837498a7f656b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371969"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: Bloqueo

En este artículo y dos artículos complementarios explican varios problemas en la programación de Windows Sockets. En este artículo se explica el bloqueo. Los otros temas se tratan en los artículos: [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md) y [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md).

Si usa o derivar de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), tendrá que administrar estos problemas por su cuenta. Si usa o derivar de la clase [CSocket](../mfc/reference/csocket-class.md), MFC administra automáticamente.

## <a name="blocking"></a>Bloqueo

Puede ser un socket en "modo de bloqueo" o "modo de no bloqueo". Las funciones de sockets en modo de bloqueo (o sincrónico) no se devuelven hasta que completan su acción. Esto se denomina bloqueo porque el socket se llamó a cuya función no puede hacer nada, se bloquea, hasta que devuelva la llamada. Una llamada a la `Receive` función miembro, por ejemplo, puede tardar un arbitrariamente mucho tiempo en completarse cuando se espera por la aplicación de envío enviar (Esto es si está usando `CSocket`, o mediante `CAsyncSocket` con el bloqueo). Si un `CAsyncSocket` objeto está en modo de no bloqueo (funciona de forma asincrónica), la llamada devuelve inmediatamente y el código de error actual, puede recuperar con el [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) es la función miembro, **WSAEWOULDBLOCK**, que indica que se habrían bloqueado la llamada si no se devuelve inmediatamente a causa del modo. (`CSocket` nunca devuelve **WSAEWOULDBLOCK**. La clase administra el bloqueo para usted.)

El comportamiento de los sockets es diferente en 32 bits y 64 bits sistemas operativos (como Windows 95 o Windows 98) que en sistemas operativos de 16 bits (por ejemplo, Windows 3.1). A diferencia de los sistemas operativos de 16 bits, los sistemas operativos de 32 bits y 64 bits utilizan la multitarea preferente y proporcionan subprocesamiento múltiple. En los sistemas operativos de 32 bits y 64 bits, puede colocar los sockets en subprocesos de trabajo independientes. Puede bloquear un socket en un subproceso sin interferir con otras actividades en la aplicación y sin necesidad de dedicar el tiempo de proceso en el bloqueo. Para obtener información sobre la programación multiproceso, consulte el artículo [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
>  En las aplicaciones multiproceso, puede usar la naturaleza de bloqueo `CSocket` para simplificar el diseño del programa sin que afecte a la capacidad de respuesta de la interfaz de usuario. Al controlar las interacciones del usuario en el subproceso principal y `CSocket` procesamiento en subprocesos alternativos, puede separar estas operaciones lógicas. En una aplicación que no es multiproceso, se deben combinar estas dos actividades y tratar como un único subproceso, lo que significa normalmente usan `CAsyncSocket` por lo que puede controlar las solicitudes de comunicaciones a petición o invalidación `CSocket::OnMessagePending` para controlar las acciones del usuario durante la actividad larga de sincrónica.

El resto de este artículo es para los programadores de sistemas operativos de 16 bits de destino:

Normalmente, si está utilizando `CAsyncSocket`, debe evitar el uso de operaciones de bloqueo y operar de forma asincrónica. En las operaciones asincrónicas, desde el punto en que se recibe un **WSAEWOULDBLOCK** código de error después de llamar a `Receive`, por ejemplo, espera hasta que su `OnReceive` función miembro se llama para notificar que puede leer de nuevo. Se realizan las llamadas asincrónicas al devolver la llamada función de notificación de devolución de llamada apropiados del socket, como [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

En Windows, las llamadas de bloqueo no es recomendable. De forma predeterminada, [CAsyncSocket](../mfc/reference/casyncsocket-class.md) admite las llamadas asincrónicas y se debe administrar el bloqueo mediante notificaciones de devolución de llamada. Clase [CSocket](../mfc/reference/csocket-class.md), por otro lado, es sincrónica. Proporciona mensajes de Windows y administrar los bloqueos.

Para obtener más información acerca del bloqueo, vea la especificación Windows Sockets. Para obtener más información acerca de "On" funciones, vea [Windows Sockets: Las notificaciones de socket](../mfc/windows-sockets-socket-notifications.md) y [Windows Sockets: Derivación de clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md).

Para obtener más información, consulte:

- [Windows Sockets: usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: fondo](../mfc/windows-sockets-background.md)

- [Windows Sockets: sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
