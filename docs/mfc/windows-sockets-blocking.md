---
title: "Windows Sockets: Bloquear | Microsoft Docs"
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
  - "modo de bloqueo de sockets"
  - "sockets [C++], comportamiento en diferentes plataformas de Windows"
  - "sockets [C++], modo de bloqueo"
  - "Windows Sockets [C++], modo de bloqueo"
  - "Windows Sockets [C++], plataformas de Windows"
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Windows Sockets: Bloquear
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo y dos casos de acompañan explican varios aspectos de la programación de Windows Sockets.  Este artículo trata el bloqueo.  Los demás problemas se cubren en los casos: [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md) y [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md).  
  
 Si usa o deriva de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), deberá administrar estos problemas personalmente.  Si usa o deriva de la clase [CSocket](../mfc/reference/csocket-class.md), MFC los administra.  
  
## Bloquear  
 Un socket puede estar en “modo de bloqueo” o “modo sin bloqueo.” Las funciones de sockets en modo de bloqueo \(o sincrónico\) no cambian hasta que se puedan realizar la acción.  Esto se denomina bloqueo porque el socket cuya función se llamó no puede hacer nada — está bloqueado — hasta la llamada vuelve.  Una llamada a la función miembro de **Recibir** , por ejemplo, podría tardar un tiempo más largo para completar mientras espera la aplicación de envío para enviar \(esto es si usa `CSocket`, o con `CAsyncSocket` con el bloqueo\).  Si un objeto de `CAsyncSocket` está en modo sin bloqueo \(que funciona de forma asincrónica\), la llamada vuelve inmediatamente y el código de error actual, recuperable mediante la función miembro de [GetLastError](../Topic/CAsyncSocket::GetLastError.md) , es **WSAEWOULDBLOCK**, que indica que la llamada habría bloqueado realizó no devolver inmediatamente debido al modo. \(`CSocket` nunca devuelve **WSAEWOULDBLOCK**.  La clase administra el bloqueo automáticamente.\)  
  
 El comportamiento de sockets es diferente en de 32 bits y sistema operativo de 64 bits \(como Windows 95 o Windows 98\) que en los sistemas operativos de 16 bits \(como Windows 3.1\).  A diferencia de los sistemas operativos de 16 bits, el de 32 bits y sistemas operativos de 64 bits utilizan multitareas prioritarias y proporcionan multithreading.  En el de 32 bits y sistema operativo de 64 bits, puede colocar los sockets en subprocesos de trabajo independientes.  Un socket en un subproceso puede bloquear sin interferir con otras actividades de la aplicación y sin pasar tiempo de cálculo del bloqueo.  Para obtener información sobre la programación multiproceso, vea el artículo [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
> [!NOTE]
>  En aplicaciones multiproceso, puede utilizar la naturaleza de bloqueo de `CSocket` para simplificar el diseño del programa sin afectar a la capacidad de respuesta de la interfaz de usuario.  Administrar interacciones del usuario en el subproceso principal y `CSocket` que procesan en subprocesos alternativos, puede separar estas operaciones lógicas.  En una aplicación que no es multiproceso, estas dos actividades se deben combinar y tratar como subproceso, que significa normalmente mediante `CAsyncSocket` de modo que puede administrar solicitudes de comunicaciones a petición, o reemplazando `CSocket::OnMessagePending` para controlar las acciones del usuario durante actividad sincrónica larga.  
  
 El resto de este tutorial es para los programadores que señalan los sistemas operativos de 16 bits:  
  
 Normalmente, si usa `CAsyncSocket`, debe evitar mediante operaciones de bloqueo y trabajar de forma asincrónica en su lugar.  En las operaciones asincrónicas, el punto en el que recibe un código de error de **WSAEWOULDBLOCK** después de llamar a **Recibir**, por ejemplo, espera hasta que la función miembro de `OnReceive` se denomina para notificarle que puede leer de nuevo.  Las llamadas asincrónicas hacen llamando a la función adecuada de notificación de devolución de llamada de socket, como [OnReceive](../Topic/CAsyncSocket::OnReceive.md).  
  
 En Windows, bloqueo llamadas se consideran práctica incorrecta.  De forma predeterminada, [CAsyncSocket](../mfc/reference/casyncsocket-class.md) admite llamadas asincrónicas, y debe administrar el bloqueo personalmente mediante notificaciones de devolución de llamada.  La clase [CSocket](../mfc/reference/csocket-class.md), por otro lado, es sincrónica.  Bombea los mensajes de Windows y administra el bloqueo para usted.  
  
 Para obtener más información sobre el bloqueo, vea la especificación de Windows Sockets.  Para obtener más información sobre las funciones de " ON ", vea [Windows Sockets: Notificaciones de socket](../mfc/windows-sockets-socket-notifications.md) y [Windows Sockets: Derivar clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CAsyncSocket::OnSend](../Topic/CAsyncSocket::OnSend.md)