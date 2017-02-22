---
title: "Windows Sockets: Notificaciones de Socket | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "notificaciones, socket"
  - "sockets [C++], notificaciones"
  - "Windows Sockets [C++], notificaciones"
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Windows Sockets: Notificaciones de Socket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe las funciones de notificación en las clases de socket.  Estas funciones miembro son funciones de devolución de llamada que el marco llama para notificar al objeto de socket de eventos importantes.  Las funciones de notificación son:  
  
-   [OnReceive](../Topic/CAsyncSocket::OnReceive.md): Notifica a este socket que hay datos en el búfer para que recupere llamando a [Recibir](../Topic/CAsyncSocket::Receive.md).  
  
-   [OnSend](../Topic/CAsyncSocket::OnSend.md): Notifica a este socket que ahora puede enviar datos llamando a [Enviar](../Topic/CAsyncSocket::Send.md).  
  
-   [OnAccept](../Topic/CAsyncSocket::OnAccept.md): Notifica a este socket que escucha que acepte pendientes solicitudes de conexión llamando a [Aceptar](../Topic/CAsyncSocket::Accept.md).  
  
-   [OnConnect](../Topic/CAsyncSocket::OnConnect.md): Notifica a este socket de conexión que el intento de conexión completa: quizás correctamente o quizás en error.  
  
-   [OnClose](../Topic/CAsyncSocket::OnClose.md): Notifica a este socket que se ha cerrado el socket que está conectado con.  
  
    > [!NOTE]
    >  Una función adicional de notificación es [OnOutOfBandData](../Topic/CAsyncSocket::OnOutOfBandData.md).  Esta notificación indica a socket que recibe que el socket de envío tiene datos “fuera de banda” para enviar.  Los datos fuera de banda es un canal lógicamente independiente asociado a cada par de sockets de secuencia conectados.  El canal fuera de banda se utiliza normalmente para enviar datos “urgentes”.  MFC admite datos fuera de banda.  Los usuarios avanzados trabajando con la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) deban utilizar el canal fuera de banda, pero se recomienda encarecidamente no usar para los usuarios de la clase [CSocket](../mfc/reference/csocket-class.md) de utilizarla.  La manera más fácil es crear un segundo socket para pasar tales datos.  Para obtener más información sobre los datos fuera de banda, vea la especificación de Windows Sockets, disponible en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Si deriva de la clase `CAsyncSocket`, debe reemplazar las funciones de notificación para esos eventos de red de interés a la aplicación.  Si deriva una clase de la clase `CSocket`, es la opción si reemplazar las funciones de notificación de interés.  También puede utilizar `CSocket` propio, en cuyo caso el valor predeterminado de las funciones de notificación a no hacer nada.  
  
 Estas funciones son funciones de devolución de llamada reemplazable.  `CAsyncSocket` y `CSocket` convierten mensajes a las notificaciones, pero debe implementar cómo responden las funciones de notificación si desea utilizarlas.  Las funciones de notificación se denominan cuando el socket se notifica de un evento de interés, como la presencia de datos que se va a leer.  
  
 MFC llama a las funciones de notificación para permitir personalizar el comportamiento de socket cuando se notifica.  Por ejemplo, podría llamar a **Recibir** de la función de notificación de `OnReceive` , es decir, en la notificación que hay datos a leer, se llama a **Recibir** para leerlo.  Este enfoque no es necesario, pero es un escenario válida.  Como alternativa, puede utilizar la función de notificación para seguir el progreso, mensajes de **trace** de impresión, etc.  
  
 Puede utilizar estas notificaciones reemplazando las funciones de notificación en una clase derivada de socket y proporcionando una implementación.  
  
 Durante una operación como recibir o envío de datos, un objeto de `CSocket` se sincrónico.  Durante el estado sincrónica, cualquier notificación lo que sucede para otros sockets se pone en cola mientras el socket actual espera la notificación que desea. \(Por ejemplo, durante una llamada de **Recibir** , el socket desea una notificación para leer.\) Una vez que el socket completa la operación síncrona y se asincrónico de nuevo, otros sockets pueden iniciar recibir notificaciones en cola.  
  
> [!NOTE]
>  En `CSocket`, la función de notificación de `OnConnect` nunca se llama.  Para las conexiones, se llama a **conectado**, que cambiarán cuando se completa la conexión \(correctamente o por error\).  Cómo se administran las notificaciones de conexión es un detalle de implementación de MFC.  
  
 Para obtener más información sobre cada función de notificación, vea la función bajo la clase `CAsyncSocket` en *la referencia de MFC*.  Para el código fuente y la información sobre ejemplos de MFC, vea [Ejemplos de MFC](../top/visual-cpp-samples.md).  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Derivar clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Cómo funcionan los sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)