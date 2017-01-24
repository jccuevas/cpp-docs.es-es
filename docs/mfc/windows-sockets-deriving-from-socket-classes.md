---
title: "Windows Sockets: Derivar de las clases de socket | Microsoft Docs"
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
  - "clases derivadas, desde clases de socket"
  - "sockets [C++], derivar desde clases de socket"
  - "Windows Sockets [C++], derivar desde clases de socket"
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Derivar de las clases de socket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe algunas funcionalidades que puede hacerse derivando dispone de la clase de una de las clases de socket.  
  
 Puede derivar dispone de clases de socket de [CAsyncSocket](../mfc/reference/casyncsocket-class.md) o de [CSocket](../mfc/reference/csocket-class.md) para agregar dispone de funcionalidad.  En particular, estas clases proporcionan a varios miembro virtual funcionan que puede reemplazar.  Estas funciones se incluyen [OnReceive](../Topic/CAsyncSocket::OnReceive.md), [OnSend](../Topic/CAsyncSocket::OnSend.md), [OnAccept](../Topic/CAsyncSocket::OnAccept.md), [OnConnect](../Topic/CAsyncSocket::OnConnect.md), y [OnClose](../Topic/CAsyncSocket::OnClose.md).  Puede reemplazar las funciones en la clase derivada de socket para aprovechar las notificaciones que proporcionan a los eventos de red aparecen.  El marco de trabajo llama a estas funciones de devolución de llamada de notificación para recibir notificaciones de los eventos importantes de socket, como la recepción de los datos que puede iniciar lectura.  Para obtener más información sobre las funciones de notificación, vea [Windows Sockets: Notificaciones de socket](../mfc/windows-sockets-socket-notifications.md).  
  
 Además, las fuentes de `CSocket` de la clase la función miembro de [OnMessagePending](../Topic/CSocket::OnMessagePending.md) \(un overridable avanzadas\).  MFC llama a esta función mientras el socket está generando mensajes basados en Windows.  Puede reemplazar `OnMessagePending` para buscar mensajes concretos de Windows y responder a ellos.  
  
 La versión predeterminada de `OnMessagePending` proporcionado en clase que `CSocket` examina la cola de mensajes para los mensajes de `WM_PAINT` mientras espera una llamada de bloqueo para completar.  Envía mensajes de dibujo para mejorar la calidad de despliegue en pantalla.  Independientemente de hacer algo útil, muestra una manera que puede que reemplace la función personalmente.  Otro ejemplo, considere el uso `OnMessagePending` para la tarea siguiente.  Suponga que mostrar un cuadro de diálogo no modal mientras espera una transacción de red para completar.  El cuadro de diálogo contiene un botón cancel que el usuario pueda utilizar para cancelar las transacciones de bloqueo que duran demasiado.  La invalidación de `OnMessagePending` podría suministrar los mensajes relacionados con este cuadro de diálogo no modal.  
  
 En la invalidación de `OnMessagePending` , devuelve **VERDADERO** o el valor devuelto de una llamada a la versión de la clase base de `OnMessagePending`.  Llame a la versión de la clase base si realiza el trabajo que desee realizar.  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)