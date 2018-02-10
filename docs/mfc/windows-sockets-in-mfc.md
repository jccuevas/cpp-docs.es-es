---
title: Windows Sockets en MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 187a58e719ad320975deba7429d6ec04a70143ac
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets en MFC
> [!NOTE]
>  MFC es compatible con Windows Sockets 1, pero no es compatible con [Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673). En primer lugar, Windows Sockets 2 incluidos con Windows 98 y es la versión incluida con Windows 2000.  
  
 MFC proporciona dos modelos para escribir programas de comunicaciones de red con Windows Sockets, incluido en dos clases MFC. Este artículo describen estos modelos y soporte técnico de sockets de MFC puede encontrar más información. Un "socket" es un extremo de comunicación: un objeto a través del cual la aplicación se comunica con otras aplicaciones de Windows Sockets a través de una red.  
  
 Para obtener información acerca de Windows Sockets, incluida una explicación del concepto de socket, consulte [Windows Sockets: fondo](../mfc/windows-sockets-background.md).  
  
##  <a name="_core_sockets_programming_models"></a>Modelos de programación de sockets  
 Los Sockets de Windows de MFC dos modelos de programación son compatibles con las clases siguientes:  
  
-   `CAsyncSocket`  
  
     Esta clase encapsula la API de Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) es para los programadores que conocer la programación de la red y desea que la flexibilidad de programar directamente con la API de sockets pero también desean la comodidad de funciones de devolución de llamada para recibir notificaciones de eventos de la red. Además de empaquetar los sockets en formato orientado a objetos para su uso en C++, la única abstracción adicional que proporciona esta clase convierte determinados mensajes de Windows relacionados con Sockets en las devoluciones de llamada. Para obtener más información, consulte [Windows Sockets: sockets de notificación](../mfc/windows-sockets-socket-notifications.md).  
  
-   `CSocket`  
  
     Esta clase deriva de `CAsyncSocket`, proporciona un mayor nivel de abstracción para trabajar con sockets mediante MFC [CArchive](../mfc/reference/carchive-class.md) objeto. Usar un socket con un archivo en gran medida es similar al uso de protocolo de serialización de archivos de MFC. Así resulta más fácil de usar que los `CAsyncSocket` modelo. [CSocket](../mfc/reference/csocket-class.md) hereda muchas funciones miembro de `CAsyncSocket` que encapsulan las API de Windows Sockets; tendrá que utilizar algunas de estas funciones y comprender por lo general de programación de sockets. Pero `CSocket` administra muchos aspectos de la comunicación que tendría que hacer usted mismo mediante la API básica o la clase `CAsyncSocket`. Lo más importante, `CSocket` proporciona bloqueo (con procesamiento en segundo plano de los mensajes de Windows), que es esencial para el funcionamiento sincrónico de `CArchive`.  
  
 Crear y usar `CSocket` y `CAsyncSocket` objetos se describe en [Windows Sockets: usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: usar clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Archivos DLL de Windows Sockets  
 Los sistemas operativos Microsoft Windows proporcionan las bibliotecas de vínculos dinámicos (DLL) de Windows Sockets. Visual C++ proporciona los archivos de encabezado adecuado y bibliotecas y la especificación de Windows Sockets.  
  
 Para obtener más información acerca de Windows Sockets, vea:  
  
-   [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows Sockets: Ejemplo de Sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Derivar de las clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Notificaciones de Socket](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows Sockets: Puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets](../mfc/windows-sockets.md)

