---
title: 'Windows Sockets: Usar Sockets con archivos | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c9956e48f88988dfec7e04cda5bba95e514ec109
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Usar sockets con archivos
Este artículo se describe la [modelo de programación de CSocket](#_core_the_csocket_programming_model). Clase [CSocket](../mfc/reference/csocket-class.md) proporciona compatibilidad con el socket en un nivel más alto de abstracción de clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket`utiliza una versión del protocolo de serialización de MFC para transferir datos hacia y desde un objeto de socket a través de MFC [CArchive](../mfc/reference/carchive-class.md) objeto. `CSocket`proporciona bloqueo (mientras administra el procesamiento en segundo plano de los mensajes de Windows) y le da acceso a `CArchive`, que administra muchos aspectos de la comunicación que tendría que hacer usted mismo mediante la API básica o la clase `CAsyncSocket`.  
  
> [!TIP]
>  Puede utilizar la clase `CSocket` por sí mismo, como una versión más cómoda de `CAsyncSocket`, pero el modelo de programación más sencillo es usar `CSocket` con un `CArchive` objeto.  
  
 Para obtener más información acerca del funcionamiento de la implementación de los sockets con archivos, consulte [Windows Sockets: funcionamiento de los Sockets con archivos de trabajo](../mfc/windows-sockets-how-sockets-with-archives-work.md). Por ejemplo de código, vea [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md) y [Windows Sockets: ejemplo de Sockets con archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md). Para obtener información acerca de algunas de las funciones que se obtiene al derivar sus propias clases de las clases de sockets, vea [Windows Sockets: derivar desde clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
> [!NOTE]
>  Si está escribiendo un programa de cliente MFC para comunicarse con servidores establecidos (no basados en MFC), no enviar objetos de C++ a través del archivo. A menos que el servidor es una aplicación MFC que entienda los tipos de objetos que desea enviar, no podrá recibir ni deserializar los objetos. Para consultar material relacionado con el asunto de la comunicación con aplicaciones no están basados en MFC, vea también el artículo [Windows Sockets: orden de bytes](../mfc/windows-sockets-byte-ordering.md).  
  
##  <a name="_core_the_csocket_programming_model"></a>El modelo de programación de CSocket  
 Mediante un `CSocket` objeto implica la creación y asociación de varios objetos de clase MFC. En el procedimiento general siguiente, cada paso se realiza por el socket de servidor y el socket de cliente, excepto el paso 3, en el que cada tipo de socket requiere una acción diferente.  
  
> [!TIP]
>  En tiempo de ejecución, la aplicación de servidor suele empezar por estar preparada y "escucha" cuando la aplicación cliente busca una conexión. Si el servidor no está preparado cuando el cliente intenta conectarse, normalmente requieren la aplicación de usuario para intentar conectarse de nuevo más tarde.  
  
#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Para establecer la comunicación entre un socket de servidor y un socket de cliente  
  
1.  Construir un [CSocket](../mfc/reference/csocket-class.md) objeto.  
  
2.  Usar el objeto para crear subyacente **SOCKET** controlar.  
  
     Para una `CSocket` objeto de cliente, normalmente, debe usar los parámetros predeterminados para [crear](../mfc/reference/casyncsocket-class.md#create), a menos que necesite un socket de datagrama. Para una `CSocket` objeto de servidor, debe especificar un puerto en el **crear** llamar.  
  
    > [!NOTE]
    >  `CArchive`no funciona con sockets de datagramas. Si desea usar `CSocket` para un socket de datagrama, debe usar la clase que se utilizaría `CAsyncSocket`, es decir, sin un archivo. Dado que los datagramas no son confiables (no garantiza que llegan y se puede repetir o desordenados), no son compatibles con la serialización a través de un archivo. Esperar a que una operación de serialización para completar de forma confiable y en orden. Si intenta usar `CSocket` con una `CArchive` de objeto para un datagrama, se produce un error en una aserción de MFC.  
  
3.  Si el socket es un cliente, llame a [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect) para conectar el objeto de socket para un socket de servidor.  
  
     O bien  
  
     Si el socket es un servidor, llame a [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen) para empezar a realizar escuchas de intentos de conexión desde un cliente. Al recibir una solicitud de conexión, aceptarla mediante una llamada a [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
    > [!NOTE]
    >  El **Accept** función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Se debe crear este objeto antes de llamar a **Accept**. Si este objeto socket se sale del ámbito, se cierra la conexión. No llame a **crear** para este nuevo objeto de socket.  
  
4.  Crear un [CSocketFile](../mfc/reference/csocketfile-class.md) objeto, asociar el `CSocket` objeto con él.  
  
5.  Crear un [CArchive](../mfc/reference/carchive-class.md) objeto para cargar (recibir) o almacenar los datos (envío). El archivo está asociado con el `CSocketFile` objeto.  
  
     Tenga en cuenta que `CArchive` no funciona con sockets de datagramas.  
  
6.  Use la `CArchive` objeto para pasar datos entre los sockets de cliente y servidor.  
  
     Tenga en cuenta que una determinada `CArchive` objeto mueve los datos en una sola dirección: para cargar (recibir) o almacenar (enviar). En algunos casos, utilizará dos `CArchive` objetos: uno para el envío de datos y otro para recibir confirmaciones.  
  
     Después de aceptar una conexión y configurar el archivo, puede realizar tareas como la validación de contraseñas.  
  
7.  Destruir del archivo, el archivo de socket y los objetos de socket.  
  
    > [!NOTE]
    >  Clase `CArchive` proporciona el `IsBufferEmpty` función miembro específicamente para su uso con la clase `CSocket`. Por ejemplo, si el búfer contiene varios mensajes de datos, necesita un bucle hasta que todos ellos se leen y se borra el búfer. En caso contrario, la siguiente notificación de que no hay datos para recibirse podría retrasarse indefinidamente. Use `IsBufferEmpty` para garantizar que recuperar todos los datos.  
  
 El artículo [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md) muestra ambos lados de este proceso con el código de ejemplo.  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../mfc/reference/csocket-class.md#create)

