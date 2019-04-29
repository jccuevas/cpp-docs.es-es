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
ms.openlocfilehash: 9992d2054c04eea1b3b63d591601acf0091acb5e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348567"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets en MFC

> [!NOTE]
>  MFC es compatible con Windows Sockets 1, pero no admite [Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2). En primer lugar, Windows Sockets 2 se incluye con Windows 98 y es la versión incluida con Windows 2000.

MFC proporciona dos modelos para escribir programas de comunicaciones de red con Sockets de Windows, incluido en dos clases MFC. En este artículo se describe estos modelos y soporte técnico de sockets de MFC puede encontrar más información. Un "socket" es un punto de conexión de comunicación: un objeto a través del cual la aplicación se comunica con otras aplicaciones de Windows Sockets a través de una red.

Para obtener información acerca de Windows Sockets, incluida una explicación del concepto de socket, vea [Windows Sockets: en segundo plano](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a> Modelos de programación de sockets

Los Sockets de Windows de MFC dos modelos de programación son compatibles con las clases siguientes:

- `CAsyncSocket`

   Esta clase encapsula la API de Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) es para los programadores que conoce la programación para redes y desean la flexibilidad de programar directamente con la API de sockets, pero también desean la comodidad de las funciones de devolución de llamada para recibir notificaciones de eventos de la red. Además de empaquetar los sockets en formato orientado a objetos para su uso en C++, la única abstracción adicional que proporciona esta clase convierte determinados mensajes de Windows relacionados con el socket en las devoluciones de llamada. Para obtener más información, consulte [Windows Sockets: Las notificaciones de socket](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Esta clase, derivada de `CAsyncSocket`, proporciona una abstracción de nivel superior para trabajar con sockets mediante MFC [CArchive](../mfc/reference/carchive-class.md) objeto. Uso de un socket con un archivo en gran medida es similar al uso de protocolo de serialización de archivos de MFC. Así resulta más fácil de usar que los `CAsyncSocket` modelo. [CSocket](../mfc/reference/csocket-class.md) hereda muchas funciones de miembro de `CAsyncSocket` que encapsulan las API de Windows Sockets; tendrá que usar algunas de estas funciones y comprender los sockets de programación general. Pero `CSocket` administra muchos aspectos de la comunicación que tendría que hacer usted mismo mediante la API sin formato o la clase `CAsyncSocket`. Lo más importante, `CSocket` proporciona bloqueo (con procesamiento en segundo plano de los mensajes de Windows), que es esencial para la operación sincrónica de `CArchive`.

Crear y usar `CSocket` y `CAsyncSocket` objetos se describe en [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Archivos DLL de Windows Sockets

Los sistemas operativos de Microsoft Windows proporcionan las bibliotecas de vínculos dinámicos (DLL) de Windows Sockets. Visual C++ proporciona los archivos de encabezado adecuados y las bibliotecas y la especificación Windows Sockets.

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
