---
title: "CSocket Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSocket class"
  - "SOCKET handle"
  - "sockets classes"
  - "WinSock CSocket class"
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSocket Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Deriva `CAsyncSocket`, hereda la encapsulación de Windows Sockets API, y representa un nivel de abstracción mayor que el de un objeto `CAsyncSocket` .  
  
## Sintaxis  
  
```  
class CSocket : public CAsyncSocket  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CSocket::CSocket](../Topic/CSocket::CSocket.md)|Crea un objeto `CSocket`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CSocket::Attach](../Topic/CSocket::Attach.md)|Asocia un identificador **SOCKET** a un objeto `CSocket` .|  
|[CSocket::CancelBlockingCall](../Topic/CSocket::CancelBlockingCall.md)|Cancela una llamada de bloqueo que está actualmente en curso.|  
|[CSocket::Create](../Topic/CSocket::Create.md)|Crea un socket.|  
|[CSocket::FromHandle](../Topic/CSocket::FromHandle.md)|Devuelve un puntero a un objeto `CSocket` , dado un identificador **SOCKET** .|  
|[CSocket::IsBlocking](../Topic/CSocket::IsBlocking.md)|Determina si una llamada de bloqueo está en curso.|  
  
### Métodos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CSocket::OnMessagePending](../Topic/CSocket::OnMessagePending.md)|Denominado para procesar pendientes mensajes mientras espera una llamada de bloqueo para completar.|  
  
## Comentarios  
 `CSocket` funciona con clases `CSocketFile` y `CArchive` para administrar el envío y recepción de datos.  
  
 Un objeto `CSocket` también proporciona el bloqueo, que es esencial para la operación síncrona `CArchive`.  Bloqueo funciona, por ejemplo `Receive`, `Send`, `ReceiveFrom`, `SendTo`, y `Accept` \(heredado desde `CAsyncSocket`\), no devuelve un error `WSAEWOULDBLOCK` en `CSocket`.  En su lugar, estas funciones esperan hasta que se complete la operación.  Además, la llamada original finalizará con el error `WSAEINTR` si se llama `CancelBlockingCall` mientras trabaja uno de ellos está bloqueando.  
  
 Para utilizar un objeto `CSocket` , llame al constructor, la llamada `Create` para crear el identificador subyacente `SOCKET` \(tipo `SOCKET`\).  Los parámetros predeterminados `Create` crean un socket de secuencia, pero si no utiliza el socket con un objeto `CArchive` , puede especificar un parámetro para crear un socket de datagrama en su lugar, o enlazado a un puerto concreto para crear un socket de servidor.  Conectar a un socket de cliente mediante `Connect` en el cliente y `Accept` en el servidor.  Cree un objeto `CSocketFile` y asociarlo al objeto `CSocket` en el constructor `CSocketFile` .  A continuación, cree un objeto `CArchive` para enviar y uno para recibir datos \(según sea necesario\), entonces los asocian con el objeto `CSocketFile` en el constructor `CArchive` .  Cuando se completan las comunicaciones, destrúyalo `CArchive`, `CSocketFile`, y los objetos `CSocket` .  Describe el tipo de datos `SOCKET` en el caso [Windows Sockets: Fondo](../../mfc/windows-sockets-background.md).  
  
 Cuando se utiliza `CArchive` con `CSocketFile` y `CSocket`, es posible que encuentre un escenario donde `CSocket::Receive` escribe un bucle \(por `PumpMessages(FD_READ)`\) que espera la cantidad solicitado de bytes.  Esto es porque el Windows Sockets sólo permite una llamada de recv por la notificación de FD\_READ, pero `CSocketFile` y `CSocket` permiten varias llamadas de recv por FD\_READ.  Si obtiene un FD\_READ cuando no hay datos para leer, la aplicación no responder.  Si no obtiene otro FD\_READ, la aplicación detiene la comunicación sobre el socket.  
  
 Puede resolver este problema como sigue.  En el método `OnReceive` de la clase de socket, llamada `CAsyncSocket::IOCtl(FIONREAD, ...)` antes de llamar al método `Serialize` de la clase de mensaje cuando los datos esperado que se leerá de socket supera el tamaño de un paquete TCP \(máximo Transmission Unit medio de red, normalmente por lo menos de 1096 bytes\).  Si el tamaño de los datos disponibles menos que se necesita, espere todos los datos que se van a recibir y inicie sólo la operación de lectura.  
  
 En el ejemplo siguiente, `m_dwExpected` es el número de bytes aproximado que el usuario espera recibir.  Se supone que lo declara en otra parte del código.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/CPP/csocket-class_1.cpp)]  
  
> [!NOTE]
>  Al utilizar los MFC sockets en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que utilice sockets para inicializar las bibliotecas de socket.  De forma predeterminada, `AfxSocketInit` sólo se llama en el subproceso primario.  
  
 Para obtener más información, vea [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Mediante sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: Cómo funcionan los sockets con archivos](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: Secuencia de operaciones](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: Ejemplo de utilizar archivos de sockets](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## Requisitos  
 **Encabezado:** afxsock.h  
  
## Vea también  
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)