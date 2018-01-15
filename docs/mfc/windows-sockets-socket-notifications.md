---
title: 'Windows Sockets: Sockets notificaciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fa9fb14dd09ace2d641fa69fa4cf39ccefeb3d01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Notificaciones de Socket
Este artículo describen las funciones de notificación en las clases de socket. Estas funciones miembro son funciones de devolución de llamada que llama el marco de trabajo para notificar al objeto socket eventos importantes. Las funciones de notificación son:  
  
-   [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): notifica a este socket que hay datos en el búfer que puede recuperar mediante una llamada a [recepción](../mfc/reference/casyncsocket-class.md#receive).  
  
-   [OnSend](../mfc/reference/casyncsocket-class.md#onsend): notifica a este socket que ahora se pueden enviar datos mediante una llamada a [enviar](../mfc/reference/casyncsocket-class.md#send).  
  
-   [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): notifica a este socket de escucha que puede aceptar solicitudes de conexión pendientes mediante una llamada a [Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
-   [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): notifica a este socket de conexión que su intento de conexión completado: quizás correctamente o quizás en error.  
  
-   [OnClose](../mfc/reference/casyncsocket-class.md#onclose): notifica a este socket que se ha cerrado el socket está conectado a.  
  
    > [!NOTE]
    >  Es una función adicional de notificación [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Esta notificación indica al socket receptor que el socket emisor tiene datos "fuera de banda" para enviar. Datos fuera de banda están un canal lógicamente independiente asociado a cada par de sockets de secuencias conectados. El canal fuera de banda normalmente se usa para enviar datos "urgentes". MFC admite datos fuera de banda. Trabajar con la clase de usuarios avanzados [CAsyncSocket](../mfc/reference/casyncsocket-class.md) quizás necesite utilizar el canal fuera de banda, pero los usuarios de la clase [CSocket](../mfc/reference/csocket-class.md) no se recomienda utilizarla. La manera más fácil es crear un segundo socket para pasar estos datos. Para obtener más información acerca de los datos fuera de banda, vea la especificación de Windows Sockets, disponible en el SDK de Windows.  
  
 Si deriva de la clase `CAsyncSocket`, debe invalidar las funciones de notificación para los eventos de interés para la aplicación de red. Si deriva una clase de la clase `CSocket`, es opcional si se debe invalidar las funciones de notificación de interés. También puede usar `CSocket` , en cuyo caso la notificación de las funciones de forma predeterminada no hace nada.  
  
 Estas funciones son funciones de devolución de llamada reemplazable. `CAsyncSocket`y `CSocket` convertir los mensajes a las notificaciones, pero debe implementar la notificación de funcionamiento de responder si desea usarlas. Se llaman a las funciones de notificación en el momento en que se notifica al socket de un evento de interés, como la presencia de datos que deben leerse.  
  
 MFC llama a las funciones de notificación que le permiten personalizar el comportamiento del socket en el momento de la notificación. Por ejemplo, puede llamar a **recepción** desde su `OnReceive` función de notificación, es decir, en que se ha notificado que hay datos que se va a leer, llamar a **recepción** para leerlo. Este enfoque no es necesario, pero es un escenario válido. Como alternativa, puede utilizar la función de notificación para seguir el progreso, imprimir **seguimiento** mensajes y así sucesivamente.  
  
 Puede aprovechar estas notificaciones reemplazando las funciones de notificación en una clase derivada de socket y proporcionar una implementación.  
  
 Durante una operación como la recepción o envío de datos, un `CSocket` objeto pasa a estado sincrónico. Durante el estado sincrónico, las notificaciones para otros sockets se ponen en cola mientras el socket actual espera la notificación que desea. (Por ejemplo, durante una **recepción** llamada, el socket desea leer una notificación.) Una vez que el socket complete la operación sincrónica y pase al estado asincrónico, otros sockets puedan comenzar a recibir las notificaciones en cola.  
  
> [!NOTE]
>  En `CSocket`, el `OnConnect` nunca se llama la función de notificación. Para las conexiones, se llama a **conectar**, que se devolverá cuando se complete la conexión (éxito o error). Cómo se administran las notificaciones de conexión es un detalle de implementación de MFC.  
  
 Para obtener más información acerca de cada función de notificación, vea la función en la clase `CAsyncSocket` en el *referencia de MFC*. Para obtener información acerca de los ejemplos MFC y código fuente, consulte [ejemplos de MFC](../visual-cpp-samples.md).  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Derivar de las clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

