---
title: 'Windows Sockets: Secuencia de operaciones'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 0f9fd339fdbdfee9381ea693568f40473c2397e9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265553"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets: Secuencia de operaciones

En este artículo se muestra, en paralelo, la secuencia de operaciones para un socket de servidor y un socket de cliente. Como los sockets utilizan `CArchive` objetos, que son necesariamente [transmitir sockets](../mfc/windows-sockets-stream-sockets.md).

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Secuencia de operaciones para una comunicación de Socket de Stream

Hasta el momento de creación de un `CSocketFile` objeto, es precisa (con algunas diferencias de parámetro) la siguiente secuencia para ambos `CAsyncSocket` y `CSocket`. Desde ese momento, la secuencia es estrictamente para `CSocket`. En la tabla siguiente se muestra la secuencia de operaciones para configurar la comunicación entre un cliente y un servidor.

### <a name="setting-up-communication-between-a-server-and-a-client"></a>Configurar la comunicación entre un servidor y un cliente

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

1. Donde *nPort* es un número de puerto. Consulte [Windows Sockets: Puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md) para obtener más información acerca de los puertos.

2. El servidor siempre debe especificar un puerto para que los clientes puedan conectarse. El `Create` llamada a veces también especifica una dirección. En el lado cliente, use los parámetros predeterminados, que indican a MFC que utilice cualquier puerto disponible.

3. Donde *nPort* es un número de puerto y *strAddr* es una dirección de equipo o una dirección de protocolo de Internet (IP).

4. Las direcciones de la máquina pueden adoptar varias formas: "ftp.microsoft.com", "microsoft.com". Las direcciones IP utilizan el formato "número de puntos", "127.54.67.32". El `Connect` función comprueba si la dirección es un número separado por puntos (aunque no se comprueba para asegurarse de que el número es un equipo válido en la red). Si no es así, `Connect` se da por supuesto un nombre de equipo de una de las otras formas.

5. Cuando se llama a `Accept` en el servidor, se pasa una referencia a un nuevo objeto de socket. Debe crear primero este objeto, pero no llame a `Create` para él. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. MFC conecta el nuevo objeto a un **SOCKET** controlar. Puede construir el socket en la pila, como se muestra, o en el montón.

6. El archivo y el archivo de socket se cierran cuando salen del ámbito. Destructor del objeto de socket también llama a la [cerrar](../mfc/reference/casyncsocket-class.md#close) función miembro para el objeto de socket cuando se sale del ámbito o se elimina el objeto.

## <a name="additional-notes-about-the-sequence"></a>Notas adicionales acerca de la secuencia

La secuencia de llamadas que se muestra en la tabla anterior es para un socket de secuencia. Sockets de datagramas que están sin conexión, no requieren la [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect), [escuchar](../mfc/reference/casyncsocket-class.md#listen), y [Accept](../mfc/reference/casyncsocket-class.md#accept) llamadas (aunque también puede usar `Connect`). En su lugar, si está utilizando la clase `CAsyncSocket`, uso de sockets de datagramas el `CAsyncSocket::SendTo` y `ReceiveFrom` funciones miembro. (Si usa `Connect` con un socket de datagrama, utilice `Send` y `Receive`.) Dado que `CArchive` no funciona con datagramas, no use `CSocket` con un archivo si el socket es un datagrama.

[CSocketFile](../mfc/reference/csocketfile-class.md) no admite todos `CFile`de funcionalidad; `CFile` miembros como `Seek`, no Asegúrese de que tiene sentido para la comunicación de socket, están disponibles. Por este motivo, algunas predeterminado MFC `Serialize` funciones no son compatibles con `CSocketFile`. Esto es particularmente cierto con las `CEditView` clase. No debe intentar serializar `CEditView` datos a través de un `CArchive` objeto asociado a un `CSocketFile` objeto mediante `CEditView::SerializeRaw`; use `CEditView::Serialize` en su lugar (no documentado). El [función SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) función espera tener funciones, como el objeto de archivo `Seek`, que `CSocketFile` no admite.

Para obtener más información, consulte:

- [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows Sockets: Sockets de Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket (clase)](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)
