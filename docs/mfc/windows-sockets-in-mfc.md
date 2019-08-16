---
title: Windows Sockets en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 44a4838a1cd863bd484701966a156be9f61f8988
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510620"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets en MFC

> [!NOTE]
>  MFC es compatible con Windows Sockets 1, pero no es compatible con [Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Windows Sockets 2 se incluyó por primera vez con Windows 98 y es la versión incluida con Windows 2000.

MFC proporciona dos modelos para escribir programas de comunicaciones de red con Windows Sockets, que se incorpora en dos clases MFC. En este artículo se describen estos modelos y más detalles sobre la compatibilidad con sockets de MFC. Un "socket" es un punto de conexión de comunicación: un objeto a través del cual la aplicación se comunica con otras aplicaciones de Windows Sockets a través de una red.

Para obtener información sobre Windows Sockets, incluida una explicación del concepto de socket, [vea Windows Sockets: En](../mfc/windows-sockets-background.md)segundo plano.

##  <a name="_core_sockets_programming_models"></a>Modelos de programación de sockets

Las siguientes clases admiten los dos modelos de programación de Windows Sockets de MFC:

- `CAsyncSocket`

   Esta clase encapsula la API de Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) es para los programadores que conocen la programación de redes y desean la flexibilidad de programar directamente en sockets API, pero que también quieren la comodidad de las funciones de devolución de llamada para la notificación de eventos de red. Aparte de empaquetar Sockets en un formulario orientado a objetos C++para su uso en, la única abstracción adicional que proporciona esta clase es convertir ciertos mensajes de Windows relacionados con el socket en devoluciones de llamada. Para obtener más información, [vea Windows Sockets: Notificaciones de socket](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Esta clase, derivada de `CAsyncSocket`, proporciona una abstracción de nivel superior para trabajar con sockets a través de un objeto [CArchive](../mfc/reference/carchive-class.md) de MFC. El uso de un socket con un archivo se parece mucho al uso del Protocolo de serialización de archivos de MFC. Esto facilita el uso que el `CAsyncSocket` modelo. [CSocket](../mfc/reference/csocket-class.md) hereda muchas funciones miembro de que `CAsyncSocket` encapsulan las API de Windows Sockets; deberá utilizar algunas de estas funciones y comprender la programación de sockets en general. Pero `CSocket` administra muchos aspectos de la comunicación que tendría que hacer mediante la API o la clase `CAsyncSocket`sin procesar. Lo más importante `CSocket` es que proporciona bloqueo (con procesamiento en segundo plano de mensajes de Windows), que es fundamental para el `CArchive`funcionamiento sincrónico de.

La creación y `CSocket` el `CAsyncSocket` uso de objetos y [se describe en Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: Usar la clase](../mfc/windows-sockets-using-class-casyncsocket.md)CAsyncSocket.

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Archivos dll de Windows Sockets

Los sistemas operativos Microsoft Windows proporcionan las bibliotecas de vínculos dinámicos (DLL) de Windows Sockets. Visual C++ proporciona las bibliotecas y los archivos de encabezado adecuados y la especificación de Windows Sockets.

Para obtener más información acerca de Windows Sockets, consulte:

- [Windows Sockets: sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: ejemplo de sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: cómo funcionan los sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: derivar desde clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: notificaciones de socket](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: bloqueo](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: ordenación de bytes](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: convertir cadenas](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: puertos y direcciones de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Vea también

[Windows Sockets](../mfc/windows-sockets.md)
