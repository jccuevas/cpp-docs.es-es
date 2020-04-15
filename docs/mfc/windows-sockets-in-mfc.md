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
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371095"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets en MFC

> [!NOTE]
> MFC admite Windows Sockets 1 pero no Windows [Sockets 2.](/windows/win32/WinSock/windows-sockets-start-page-2) Windows Sockets 2 se incluye por primera vez con Windows 98 y es la versión incluida con Windows 2000.

MFC proporciona dos modelos para escribir programas de comunicaciones de red con Windows Sockets, incorporados en dos clases MFC. En este artículo se describen estos modelos y más detalles compatibilidad con sockets MFC. Un "socket" es un punto de conexión de comunicación: un objeto a través del cual la aplicación se comunica con otras aplicaciones de Windows Sockets a través de una red.

Para obtener información sobre Windows Sockets, incluida una explicación del concepto de socket, vea [Windows Sockets: Background](../mfc/windows-sockets-background.md).

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>Modelos de programación de sockets

Las clases siguientes admiten los dos modelos de programación de Windows Sockets de MFC:

- `CAsyncSocket`

   Esta clase encapsula la API de Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) es para programadores que conocen la programación de red y desean la flexibilidad de programar directamente a la API de sockets, pero también quieren la comodidad de las funciones de devolución de llamada para la notificación de eventos de red. Aparte de empaquetar sockets en formato orientado a objetos para su uso en C++, la única abstracción adicional que proporciona esta clase es convertir determinados mensajes de Windows relacionados con sockets en devoluciones de llamada. Para obtener más información, consulte [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Esta clase, derivada `CAsyncSocket`de , proporciona una abstracción de nivel superior para trabajar con sockets a través de un objeto [CArchive](../mfc/reference/carchive-class.md) de MFC. El uso de un socket con un archivo se asemeja mucho al uso del protocolo de serialización de archivos de MFC. Esto hace que sea `CAsyncSocket` más fácil de usar que el modelo. [CSocket](../mfc/reference/csocket-class.md) hereda muchas `CAsyncSocket` funciones miembro de que encapsulan las API de Windows Sockets; tendrá que utilizar algunas de estas funciones y entender la programación de sockets en general. Pero `CSocket` administra muchos aspectos de la comunicación que tendría que `CAsyncSocket`hacer usted mismo utilizando la API sin procesar o la clase. Lo más `CSocket` importante, proporciona bloqueo (con procesamiento en segundo plano `CArchive`de mensajes de Windows), que es esencial para el funcionamiento sincrónico de .

La creación `CSocket` `CAsyncSocket` y el uso de objetos se describe en [Windows Sockets: Uso](../mfc/windows-sockets-using-sockets-with-archives.md) de sockets con archivos y Windows Sockets: uso de [la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Archivos DLL de Windows Sockets

Los sistemas operativos Microsoft Windows proporcionan las bibliotecas de vínculos dinámicos (DLL) de Windows Sockets. Visual C++ proporciona los archivos de encabezado y bibliotecas adecuados y la especificación de Windows Sockets.

Para obtener más información acerca de Windows Sockets, consulte:

- [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: Ejemplo de sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Derivar de las clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Notificaciones de Socket](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: Puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets](../mfc/windows-sockets.md)
