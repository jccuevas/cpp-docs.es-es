---
title: "Windows Sockets en MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], Windows Sockets"
  - "sockets [C++], MFC"
  - "sockets [C++], modelos de programación"
  - "Windows Sockets [C++], compatibilidad con MFC"
  - "Windows Sockets [C++], modelos de programación"
  - "WINSOCK.DLL"
  - "WSOCK32.DLL"
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  MFC admite el Windows Sockets 1 pero no admite [Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  El Windows Sockets 2 primero enviado con Windows 98 y es la versión que se incluye con Windows 2000.  
  
 MFC proporciona dos modelos para escribir programas de comunicaciones por red con Windows Sockets, personificados a dos clases MFC.  En este artículo se describe la compatibilidad de los MFC sockets de estos modelos y detalles adicionales.  Un “socket” es un extremo de comunicación: un objeto a través del que la aplicación se comunica con otras aplicaciones de Windows Sockets a través de una red.  
  
 Para obtener información en Windows Sockets, incluyendo una explicación del concepto de socket, vea [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md).  
  
##  <a name="_core_sockets_programming_models"></a> Modelos de programación de sockets  
 Los dos modelos de programación de Windows Sockets de MFC admite las siguientes clases:  
  
-   `CAsyncSocket`  
  
     Esta clase encapsula el Windows Sockets API.  [CAsyncSocket](../mfc/reference/casyncsocket-class.md) es para los programadores que conocen la programación de red y desea que la flexibilidad de la programación directa a sockets API pero también desea comodidad de funciones de devolución de llamada para notificaciones de los eventos de la red.  Distinto de sockets de paquete en el formulario orientado para el uso en C\+\+, la única manera adicional fuentes de esta clase está desarrollando determinados mensajes socket\- de Windows relacionados en las devoluciones de llamada.  Para obtener más información, vea [Windows Sockets: Notificaciones de socket](../mfc/windows-sockets-socket-notifications.md).  
  
-   `CSocket`  
  
     Esta clase, derivada de `CAsyncSocket`, proporciona una abstracción de alto nivel para ejecutar sockets a través de un objeto de MFC [CArchive](../mfc/reference/carchive-class.md) .  Mediante un socket con un archivo se parece mucho mediante el protocolo de serialización del archivo de MFC.  Esto hace más fácil de usar que el modelo de `CAsyncSocket` .  [CSocket](../mfc/reference/csocket-class.md) hereda muchas funciones miembro de `CAsyncSocket` que encapsulan el Windows Sockets API; tendrá que utilizar algunas de estas funciones y entender los sockets que programan normalmente.  Pero `CSocket` administra muchos aspectos de comunicación que tendría que hacerse mediante la API sin formato o la clase `CAsyncSocket`.  Más importante, `CSocket` proporciona el bloqueo \(con el procesamiento en segundo plano de mensajes de Windows\), que es esencial para la operación síncrona de `CArchive`.  
  
 Crear y utilizar `CSocket` y los objetos de `CAsyncSocket` se describe en [Windows Sockets: Mediante sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) y [Windows Sockets: Mediante la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Archivos DLL de Windows Sockets  
 Los sistemas operativos Microsoft Windows proporcionan las bibliotecas de vínculos dinámicos \(DLL\) de Windows Sockets.  Visual C\+\+ proporciona los archivos de encabezado y bibliotecas adecuadas y la especificación de Windows Sockets.  
  
> [!NOTE]
>  En Windows NT y Windows 2000, la compatibilidad de Windows Sockets para las aplicaciones de 16 bits se basa en WINSOCK.DLL.  Para las aplicaciones de 32 bits, compatibilidad está en WSO CK32 .DLL.  El proporcionadas son idénticos salvo que las versiones de 32 bits tienen parámetros ensanchadas a 32 bits.  En Win32, se proporciona seguridad para subprocesos.  
  
 Para obtener más información sobre Windows Sockets, vea:  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows Sockets: Ejemplo de sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets: Cómo funcionan los sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Derivar clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Notificaciones de socket](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows Sockets: Puertos y direcciones de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## Vea también  
 [Windows Sockets](../mfc/windows-sockets.md)