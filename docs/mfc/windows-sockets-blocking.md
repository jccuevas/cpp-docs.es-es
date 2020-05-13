---
title: 'Windows Sockets: Bloquear'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359995"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: Bloquear

Este artículo y dos artículos complementarios explican varios problemas en la programación de Windows Sockets. Este artículo trata el bloqueo. Los otros problemas se tratan en los artículos: [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) y Windows [Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Si usa o deriva de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), deberá administrar estos problemas usted mismo. Si utiliza o deriva de la clase [CSocket](../mfc/reference/csocket-class.md), MFC los administra por usted.

## <a name="blocking"></a>Bloqueos

Un socket puede estar en "modo de bloqueo" o "modo sin bloqueo." Las funciones de sockets en modo de bloqueo (o sincrónico) no se devuelven hasta que pueden completar su acción. Esto se denomina bloqueo porque el socket cuya función se llamó no puede hacer nada (está bloqueado) hasta que se devuelve la llamada. Una llamada `Receive` a la función miembro, por ejemplo, puede tardar un tiempo arbitrariamente largo para completar se `CSocket`completa `CAsyncSocket` a medida que espera a que la aplicación de envío para enviar (esto es si está utilizando , o utilizando con bloqueo). Si `CAsyncSocket` un objeto está en modo de no bloqueo (operando de forma asincrónica), la llamada devuelve inmediatamente y el código de error actual, recuperable con la función miembro [GetLastError,](../mfc/reference/casyncsocket-class.md#getlasterror) es **WSAEWOULDBLOCK**, lo que indica que la llamada se habría bloqueado si no se hubiera devuelto inmediatamente debido al modo. (`CSocket` Nunca devuelve **WSAEWOULDBLOCK**. La clase administra el bloqueo por usted.)

El comportamiento de los sockets es diferente en sistemas operativos de 32 bits y 64 bits (como Windows 95 o Windows 98) que en sistemas operativos de 16 bits (como Windows 3.1). A diferencia de los sistemas operativos de 16 bits, los sistemas operativos de 32 y 64 bits utilizan multitarea preventiva y proporcionan multiproceso. En los sistemas operativos de 32 y 64 bits, puede colocar los sockets en subprocesos de trabajo independientes. Un socket en un subproceso puede bloquearse sin interferir con otras actividades de la aplicación y sin gastar tiempo de proceso en el bloqueo. Para obtener información sobre la programación multiproceso, consulte el artículo [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
> En aplicaciones multiproceso, puede utilizar la `CSocket` naturaleza de bloqueo de para simplificar el diseño de su programa sin afectar a la capacidad de respuesta de la interfaz de usuario. Al controlar las interacciones del `CSocket` usuario en el subproceso principal y procesar en subprocesos alternativos, puede separar estas operaciones lógicas. En una aplicación que no es multiproceso, estas dos actividades deben combinarse y `CAsyncSocket` controlarse como un único subproceso, `CSocket::OnMessagePending` lo que normalmente significa usar para que pueda controlar las solicitudes de comunicaciones a petición o reemplazar para controlar las acciones del usuario durante una actividad sincrónica prolongada.

El resto de esta discusión es para programadores dirigidos a sistemas operativos de 16 bits:

Normalmente, si `CAsyncSocket`está utilizando , debe evitar el uso de operaciones de bloqueo y operar de forma asincrónica en su lugar. En operaciones asincrónicas, desde el punto en el que recibe `Receive`un código de error `OnReceive` **WSAEWOULDBLOCK** después de llamar , por ejemplo, espere hasta que se llame a la función miembro para notificarle que puede leer de nuevo. Las llamadas asincrónicas se realizan llamando a la función de notificación de devolución de llamada adecuada del socket, como [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

En Windows, las llamadas de bloqueo se consideran malas prácticas. De forma predeterminada, [CAsyncSocket](../mfc/reference/casyncsocket-class.md) admite llamadas asincrónicas y debe administrar el bloqueo mediante notificaciones de devolución de llamada. La clase [CSocket](../mfc/reference/csocket-class.md), por otro lado, es sincrónica. Bombea mensajes de Windows y administra el bloqueo para usted.

Para obtener más información acerca del bloqueo, consulte la especificación de Windows Sockets. Para obtener más información acerca de las funciones "On", vea [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md) y [Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

Para más información, consulte:

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
