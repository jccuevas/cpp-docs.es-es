---
title: 'Windows Sockets: Secuencia de operaciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f70765d94b0104cf905130ce043c2b0e35b26a41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets: Secuencia de operaciones
En este artículo se muestra, en paralelo, la secuencia de operaciones para un socket de servidor y un socket de cliente. Como los sockets utilizan `CArchive` objetos, son necesariamente [sockets de secuencia](../mfc/windows-sockets-stream-sockets.md).  
  
## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Secuencia de operaciones para una comunicación de Socket de secuencia  
 Hasta el momento de creación de un `CSocketFile` objeto, la siguiente secuencia será precisa (con algunas diferencias de parámetro) para ambos `CAsyncSocket` y `CSocket`. Desde ese momento, la secuencia está estrictamente destinado para `CSocket`. La tabla siguiente muestra la secuencia de operaciones para configurar la comunicación entre un cliente y un servidor.  
  
### <a name="setting-up-communication-between-a-server-and-a-client"></a>Configuración de la comunicación entre un servidor y un cliente  
  
|Servidor|Cliente|  
|------------|------------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> O bien<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - o ambos:|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> O bien<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - o ambos:|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> O bien<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> O bien<br /><br /> `arOut << dwValue;`6|  
  
 1. Donde `nPort` es un número de puerto. Vea [Windows Sockets: puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md) para obtener más información acerca de los puertos.  
  
 2. El servidor siempre debe especificar un puerto para que los clientes puedan conectarse. El **crear** llamada a veces también especifica una dirección. En el lado del cliente, use los parámetros predeterminados, que indican a MFC que utilice cualquier puerto disponible.  
  
 3. Donde `nPort` es un número de puerto y *strAddr* es una dirección de equipo o una dirección de protocolo de Internet (IP).  
  
 4. Direcciones de máquina pueden adoptar varias formas: "ftp.microsoft.com", "microsoft.com". Direcciones IP utilizan el formato "número de puntos" "127.54.67.32". El **conectar** función comprueba si la dirección es un número con puntos (aunque no se comprueba para asegurarse de que el número es un equipo válido en la red). Si no es así, **conectar** se da por supuesto un nombre de equipo de una de las otras formas.  
  
 5. Cuando se llama a **Accept** en el servidor, se pasa una referencia a un nuevo objeto de socket. Debe crear este objeto en primer lugar, pero no llame a **crear** para él. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. MFC conecta el nuevo objeto a una **SOCKET** controlar. Puede crear el socket en la pila, tal como se muestra, o en el montón.  
  
 6. El archivo y el archivo de socket se cierran cuando salen del ámbito. Destructor del objeto de socket también llama el [cerrar](../mfc/reference/casyncsocket-class.md#close) función de miembro para el objeto de socket cuando el objeto queda fuera del ámbito o se elimina.  
  
## <a name="additional-notes-about-the-sequence"></a>Notas adicionales acerca de la secuencia  
 La secuencia de llamadas que se muestra en la tabla anterior es para un socket de secuencia. Sockets de datagrama, que están sin conexión, no requieren la [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect), [escuchar](../mfc/reference/casyncsocket-class.md#listen), y [Accept](../mfc/reference/casyncsocket-class.md#accept) llamadas (aunque también puede usar **Conectar**). En su lugar, si está utilizando una clase `CAsyncSocket`, sockets de datagramas usan el `CAsyncSocket::SendTo` y `ReceiveFrom` funciones miembro. (Si usa **conectar** con un socket de datagrama, use **enviar** y **recepción**.) Dado que `CArchive` no funciona con datagramas, no use `CSocket` con un archivo si el socket es un datagrama.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) no admitir todas `CFile`de funcionalidad; `CFile` miembros como `Seek`, que no tengan ningún sentido para una comunicación de socket, no están disponibles. Por este motivo, algunas predeterminado MFC `Serialize` funciones no son compatibles con `CSocketFile`. Esto es especialmente así la `CEditView` clase. No debe intentar serializar `CEditView` datos a través de un `CArchive` objeto asociado a un `CSocketFile` objeto mediante la `CEditView::SerializeRaw`; use **CEditView** en su lugar (no documentados). El [función SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) función espera el objeto de archivo tenga funciones, como `Seek`, que `CSocketFile` no admite.  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket (clase)](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)   
 [CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)

