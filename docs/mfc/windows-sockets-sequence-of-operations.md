---
title: "Windows Sockets: Secuencia de operaciones | Microsoft Docs"
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
  - "sockets [C++], operaciones"
  - "sockets [C++], sockets de secuencia"
  - "sockets de secuencia [C++]"
  - "Windows Sockets [C++], operaciones"
  - "Windows Sockets [C++], sockets de secuencia"
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Secuencia de operaciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se muestra, en paralelo, la secuencia de operaciones para un socket de servidor y un socket de cliente.  Dado que los sockets utilizan objetos de `CArchive` , son necesariamente [sockets de secuencia](../mfc/windows-sockets-stream-sockets.md).  
  
## Secuencia de operaciones para una comunicación de socket de secuencia  
 Hasta el punto de construir un objeto de `CSocketFile` , la secuencia siguiente es exacta \(con algunas diferencias de parámetro\) para `CAsyncSocket` y `CSocket`.  A partir de ese momento, la secuencia está estrictamente para `CSocket`.  La tabla siguiente muestra la secuencia de operaciones para colocar la comunicación entre un cliente y un servidor.  
  
### Comunicación entre la creación un Servidor y un cliente  
  
|Servidor|Cliente|  
|--------------|-------------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file,`  `CArchive::load);`<br /><br /> O bien<br /><br /> `CArchive arOut(&file,`  `CArchive::store);`<br /><br /> – ambos –|`// construct an archive`<br /><br /> `CArchive arIn(&file,`  `CArchive::load);`<br /><br /> O bien<br /><br /> `CArchive arOut(&file,`  `CArchive::store);`<br /><br /> – ambos –|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> O bien<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> O bien<br /><br /> `arOut << dwValue;`6|  
  
 1.  Donde es un número de puerto `nPort` .  Vea [Windows Sockets: Puertos y direcciones de socket](../mfc/windows-sockets-ports-and-socket-addresses.md) para obtener más información sobre puertos.  
  
 2.  El servidor debe especificar siempre un puerto para que los clientes pueden conectarse.  La llamada de **crear** a veces también especifica una dirección.  En el cliente, utilice los parámetros predeterminados, que pide a MFC utiliza cualquier puerto disponible.  
  
 3.  Donde es `nPort` un número de puerto y *un strAddr* es una dirección de equipo o dirección de \(IP\) de protocolo de Internet.  
  
 4.  Las direcciones de equipo pueden tomar varios formularios: “ftp.microsoft.com”, “microsoft.com”.  Las direcciones IP utilizan el formato “127.54.67.32” “número dotted”.  Los controles de ejecución de **conectado** comprueba si la dirección es un número dotted \(aunque no comprueba para asegurarse el número son equipo válido en la red\).  Si no, **conectado** supone un nombre de equipo de uno de los otros formularios.  
  
 5.  Cuando se llama a **Aceptar** en el servidor, se pasa una referencia a un nuevo objeto de socket.  Debe construir este objeto primero, pero no llama a **crear** para él.  Tenga presente que si este objeto de socket sale del ámbito, la conexión se cierra.  MFC conecta el nuevo objeto a un identificador de **SOCKET** .  Puede crear el socket en la pila, como se muestra, o en la pila.  
  
 6.  El archivo y el archivo de socket se cierran cuando salen del ámbito.  El destructor del objeto de socket también llama a la función miembro de [cerrar](../Topic/CAsyncSocket::Close.md) para el objeto de socket cuando el objeto salga del ámbito o eliminan.  
  
## Notas adicionales Sobre la secuencia  
 La secuencia de llamadas que se muestran en la tabla anterior es para un socket de secuencia.  Los sockets de datagrama, que se sines conexión, no requieren [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md), [Escucha](../Topic/CAsyncSocket::Listen.md), y las llamadas de [Aceptar](../Topic/CAsyncSocket::Accept.md) \(aunque puede utilizar opcionalmente **conectado**\).  En su lugar, si utiliza la clase `CAsyncSocket`, sockets de datagrama utilizan `CAsyncSocket::SendTo` y el miembro de `ReceiveFrom` funciona. \(Si usa **conectado** con un socket de datagrama, se utiliza **Enviar** y **Recibir**.\) Dado que `CArchive` no funciona con los datagramas, no utilice `CSocket` con un archivo si el socket es un datagrama.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) no admite toda la funcionalidad de `CFile` ; los miembros de `CFile` como `Seek`, que no tienen ningún sentido para una comunicación de socket, no están disponibles.  Debido a esto, algunas funciones de MFC `Serialize` predeterminado no son compatibles con `CSocketFile`.  Esto es especialmente cierto de la clase de `CEditView` .  No debe intentar serializar los datos de `CEditView` a través de un objeto de `CArchive` asociado a un objeto de `CSocketFile` mediante `CEditView::SerializeRaw`; uso **CEditView::Serialize** en su lugar \(no documentado\).  La función de [SerializeRaw](../Topic/CEditView::SerializeRaw.md) espera que el objeto de archivo tiene funciones, como `Seek`, que `CSocketFile` no admite.  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Puertos y direcciones de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket Class](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)   
 [CAsyncSocket::Close](../Topic/CAsyncSocket::Close.md)