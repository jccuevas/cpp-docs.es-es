---
title: "Windows Sockets: Usar Sockets con archivos | Microsoft Docs"
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
  - "archivos [C++], y Windows Sockets"
  - "CSocket (clase), modelo de programación"
  - "sockets [C++], que contengan archivos"
  - "Windows Sockets [C++], archivos"
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Usar Sockets con archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe [Modelo de programación de CSocket](#_core_the_csocket_programming_model).  Compatibilidad de socket de fuentes de [CSocket](../mfc/reference/csocket-class.md) de clase en un nivel alto de abstracción que la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md).  `CSocket` utiliza una versión del protocolo de serialización de MFC para pasar los datos entre un objeto de socket a través de un objeto de MFC [CArchive](../mfc/reference/carchive-class.md) .  `CSocket` proporciona el bloqueo \(mientras controla el procesamiento en segundo plano de mensajes de Windows\) y proporciona acceso a `CArchive`, que administra muchos aspectos de comunicación que tendría que hacerse mediante la API sin formato o la clase `CAsyncSocket`.  
  
> [!TIP]
>  Puede utilizar la clase `CSocket` por sí mismo, como versión más conveniente de `CAsyncSocket`, pero el modelo de programación más sencillo es utilizar `CSocket` con un objeto de `CArchive` .  
  
 Para obtener más información sobre cómo funciona la implementación de sockets con archivos, vea [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md).  Por ejemplo, vea [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md) y [Windows Sockets: Ejemplo de Sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md).  Para obtener información sobre algunas funcionalidades que puede hacerse derivando dispone de clases de las clases MFC sockets, vea [Windows Sockets: Derivar de las clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
> [!NOTE]
>  Si está escribiendo un programa cliente de MFC para comunicarse con los servidores establecidos \(de no MFC\), no envíe los objetos de C\+\+ a través del archivo.  A menos que el servidor es una aplicación MFC que entienda las clases de objetos desee enviar, no podrá recibir y deserializar objetos.  Para el material relacionado a propósito de comunicarse con aplicaciones de no MFC, vea también el artículo [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md).  
  
##  <a name="_core_the_csocket_programming_model"></a> El modelo de programación de CSocket  
 Utilizando un objeto de `CSocket` requiere crear y el asociar juntos de varios objetos de clases MFC.  En el procedimiento general siguiente, cada medida es realizada por el socket de servidor y el socket de cliente, a excepción del paso 3, en el que cada tipo de socket requiere una acción diferente.  
  
> [!TIP]
>  En tiempo de ejecución, la aplicación de servidor inicia primero para ser lista y “que escucha” cuando la aplicación cliente busca una conexión.  Si el servidor no está listo cuando el cliente intenta conectarse, se exige la aplicación de usuario para probar la conexión de nuevo más adelante.  
  
#### Para configurar la comunicación entre un socket de servidor y un socket de cliente  
  
1.  Crea un objeto de [CSocket](../mfc/reference/csocket-class.md) .  
  
2.  Utilice el objeto para crear el identificador subyacente de **SOCKET** .  
  
     Para un objeto de cliente `CSocket` , debe usar normalmente los parámetros predeterminados a [crear](../Topic/CAsyncSocket::Create.md), a menos que necesite un socket de datagrama.  Para un objeto de servidor de `CSocket` , debe especificar un puerto en la llamada de **crear** .  
  
    > [!NOTE]
    >  `CArchive` no funciona con los sockets de datagrama.  Si desea utilizar `CSocket` para un socket de datagrama, debe usar la clase como utilizaría `CAsyncSocket`, es decir, sin un archivo.  Dado que los datagramas no son predecibles \(no garantizado para proteger y se puede repetir o desordenados\), no son compatibles con la serialización a través de un archivo.  Se espera que una operación de serialización complete confiabilidad y en orden.  Si intenta utilizar `CSocket` con un objeto de `CArchive` para un datagrama, una aserción de MFC produce un error.  
  
3.  Si el socket es un cliente, llamada [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md) para conectar el objeto de socket a un socket de servidor.  
  
     O bien  
  
     Si el socket es un servidor, llamada [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md) a iniciar la escucha de intenta conectarse desde un cliente.  Al recibir una solicitud de conexión, aceptela llamando a [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md).  
  
    > [!NOTE]
    >  La función miembro de **Aceptar** toma una referencia a un nuevo, vacío objeto de `CSocket` como parámetro.  Debe construir este objeto antes de llamar a **Aceptar**.  Si este objeto de socket sale del ámbito, la conexión se cierra.  No llame a **crear** para este nuevo objeto de socket.  
  
4.  Cree un objeto de [CSocketFile](../mfc/reference/csocketfile-class.md) , asociando el objeto de `CSocket` al.  
  
5.  Cree un objeto de [CArchive](../mfc/reference/carchive-class.md) de carga \(receptora\) o almacenar datos \(de transporte\).  El archivo se asocia el objeto de `CSocketFile` .  
  
     Tenga presente que `CArchive` no funciona con los sockets de datagrama.  
  
6.  Utilice el objeto de `CArchive` a los datos del paso entre el cliente y los sockets de servidor.  
  
     Tenga en cuenta que un objeto especificado de `CArchive` mueve datos solo en una dirección: para cargar \(receptora\) o almacenar \(transporte\).  En algunos casos, utilizará dos objetos de `CArchive` : uno para enviar datos, otro para recibir acuses de recepción.  
  
     Después de aceptar una conexión y de colocar el archivo, puede realizar tareas como validando contraseñas.  
  
7.  Destruya el archivo, el archivo de socket, y los objetos de socket.  
  
    > [!NOTE]
    >  Fuentes de `CArchive` de la clase la función miembro de `IsBufferEmpty` específicamente para el uso con la clase `CSocket`.  Si el búfer contiene mensajes de datos, por ejemplo, necesita recorrer hasta que se lean todos y se borra el búfer.  Si no, la notificación siguiente que hay datos que se van a recibir puede ser y indefinidamente.  Utilice `IsBufferEmpty` para garantizar que recupera todos los datos.  
  
 El artículo [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md) muestra ambos lados de este proceso con código de ejemplo.  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../Topic/CSocket::Create.md)