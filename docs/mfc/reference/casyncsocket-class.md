---
title: "CAsyncSocket Class | Microsoft Docs"
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
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous Windows Sockets"
  - "CAsyncSocket class"
  - "comunicaciones [C++], red"
  - "network communications"
  - "sockets [C++], Windows"
  - "Windows Sockets [C++], asincrónico"
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
caps.latest.revision: 23
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAsyncSocket Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un socket de Windows — un extremo de comunicación por red.  
  
## Sintaxis  
  
```  
class CAsyncSocket : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::CAsyncSocket](../Topic/CAsyncSocket::CAsyncSocket.md)|Crea un objeto `CAsyncSocket`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md)|acepta una conexión en el socket.|  
|[CAsyncSocket::AsyncSelect](../Topic/CAsyncSocket::AsyncSelect.md)|solicita la notificación de eventos para el socket.|  
|[CAsyncSocket::Attach](../Topic/CAsyncSocket::Attach.md)|Asocia un identificador de socket a un objeto de `CAsyncSocket` .|  
|[CAsyncSocket::Bind](../Topic/CAsyncSocket::Bind.md)|Asocia una dirección local al socket.|  
|[CAsyncSocket::Close](../Topic/CAsyncSocket::Close.md)|Cierre el socket.|  
|[CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)|Establece una conexión a un socket del mismo nivel.|  
|[CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)|crea un socket.|  
|[CAsyncSocket::Detach](../Topic/CAsyncSocket::Detach.md)|Desasocia un identificador de socket de un objeto de `CAsyncSocket` .|  
|[CAsyncSocket::FromHandle](../Topic/CAsyncSocket::FromHandle.md)|Devuelve un puntero a un objeto de `CAsyncSocket` , dado un identificador de socket.|  
|[CAsyncSocket::GetLastError](../Topic/CAsyncSocket::GetLastError.md)|Obtiene el estado de error de la última operación que produjo un error.|  
|[CAsyncSocket::GetPeerName](../Topic/CAsyncSocket::GetPeerName.md)|Obtiene la dirección del socket del mismo nivel con el que el socket está conectado.|  
|[CAsyncSocket::GetPeerNameEx](../Topic/CAsyncSocket::GetPeerNameEx.md)|Obtiene la dirección del socket del mismo nivel con el que el socket está conectado \(las direcciones de IPv6 de identificadores\).|  
|[CAsyncSocket::GetSockName](../Topic/CAsyncSocket::GetSockName.md)|obtiene el nombre local para un socket.|  
|[CAsyncSocket::GetSockNameEx](../Topic/CAsyncSocket::GetSockNameEx.md)|Obtiene el nombre local para un socket \(direcciones de IPv6 de identificadores\).|  
|[CAsyncSocket::GetSockOpt](../Topic/CAsyncSocket::GetSockOpt.md)|Recupera una opción de socket.|  
|[CAsyncSocket::IOCtl](../Topic/CAsyncSocket::IOCtl.md)|Controla el modo de socket.|  
|[CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)|Establece un socket para realizar escuchas para las solicitudes de conexión entrante.|  
|[CAsyncSocket::Receive](../Topic/CAsyncSocket::Receive.md)|Recibe datos de socket.|  
|[CAsyncSocket::ReceiveFrom](../Topic/CAsyncSocket::ReceiveFrom.md)|Recibe un datagrama y almacena la dirección de origen.|  
|[CAsyncSocket::ReceiveFromEx](../Topic/CAsyncSocket::ReceiveFromEx.md)|Recibe un datagrama y almacena la dirección de origen \(direcciones de IPv6 de identificadores\).|  
|[CAsyncSocket::Send](../Topic/CAsyncSocket::Send.md)|Envía los datos a un socket conectado.|  
|[CAsyncSocket::SendTo](../Topic/CAsyncSocket::SendTo.md)|Envía los datos a un destino concreto.|  
|[CAsyncSocket::SendToEx](../Topic/CAsyncSocket::SendToEx.md)|Envía los datos a un destino concreto \(direcciones de IPv6 de identificadores\).|  
|[CAsyncSocket::SetSockOpt](../Topic/CAsyncSocket::SetSockOpt.md)|Establece una opción de socket.|  
|[CAsyncSocket::ShutDown](../Topic/CAsyncSocket::ShutDown.md)|deshabilita las llamadas de **Enviar** y\/o de **Recibir** en el socket.|  
|[CASyncSocket::Socket](../Topic/CASyncSocket::Socket.md)|Asigna un identificador de socket.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](../Topic/CAsyncSocket::OnAccept.md)|Notifica un socket que escucha que acepte pendientes solicitudes de conexión llamando a **acepte**.|  
|[CAsyncSocket::OnClose](../Topic/CAsyncSocket::OnClose.md)|Notifica un socket que se ha cerrado el socket conectado a él.|  
|[CAsyncSocket::OnConnect](../Topic/CAsyncSocket::OnConnect.md)|Notifica un socket de conexión que el intento de conexión está completo, si correctamente o de error.|  
|[CAsyncSocket::OnOutOfBandData](../Topic/CAsyncSocket::OnOutOfBandData.md)|Notifica un socket que recibe que hay datos fuera de banda que se leerán del socket, normalmente un mensaje urgente.|  
|[CAsyncSocket::OnReceive](../Topic/CAsyncSocket::OnReceive.md)|Notifica un socket que escucha que hay datos que se recuperarán llamando a **Recibir**.|  
|[CAsyncSocket::OnSend](../Topic/CAsyncSocket::OnSend.md)|Notifica un socket que puede enviar datos llamando a **Enviar**.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::operator \=](../Topic/CAsyncSocket::operator%20=.md)|asigna un nuevo valor a un objeto de `CAsyncSocket` .|  
|[CAsyncSocket::operator SOCKET](../Topic/CAsyncSocket::operator%20SOCKET.md)|Este operador se utiliza para recuperar el identificador de **SOCKET** del objeto de `CAsyncSocket` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::m\_hSocket](../Topic/CAsyncSocket::m_hSocket.md)|Indica el identificador de **SOCKET** asociado a este objeto de `CAsyncSocket` .|  
  
## Comentarios  
 La clase `CAsyncSocket` encapsula las funciones API de socket de Windows, proporcionando una abstracción orientado para programadores que desean utilizar el Windows Sockets junto con MFC.  
  
 Esta clase se basa en la suposición de que entiende comunicaciones por red.  Es responsable de administrar el bloqueo, diferencias de orden de bytes, y conversiones entre Unicode y cadenas de juego de caracteres multibyte \(MBCS\).  Si desea una interfaz más conveniente administrar estos problemas para usted, vea la clase [CSocket](../../mfc/reference/csocket-class.md).  
  
 Para utilizar un objeto de `CAsyncSocket` , llamar a su constructor, entonces para llamar a la función de [Crear](../Topic/CAsyncSocket::Create.md) para crear el identificador subyacente de socket \(tipo `SOCKET`\), excepto en sockets aceptados.  Para una llamada de socket de servidor la función miembro de [Escucha](../Topic/CAsyncSocket::Listen.md) , y para una llamada de socket de cliente la función miembro de [Conectar](../Topic/CAsyncSocket::Connect.md) .  El socket de servidor debe llamar a la función de [acepte](../Topic/CAsyncSocket::Accept.md) al recibir una solicitud de conexión.  Utilice las funciones restantes de `CAsyncSocket` para realizar comunicaciones entre sockets.  Al finalizar, destruya el objeto de `CAsyncSocket` si se ha creado en la pila; destructor llama automáticamente a la función de [Cerrar](../Topic/CAsyncSocket::Close.md) .  Describe el tipo de datos de `SOCKET` en el caso [Windows Sockets: Fondo](../../mfc/windows-sockets-background.md).  
  
> [!NOTE]
>  Al utilizar los MFC sockets en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que utilice sockets para inicializar las bibliotecas de socket.  De forma predeterminada, `AfxSocketInit` sólo se llama en el subproceso primario.  
  
 Para obtener más información, vea [Windows Sockets: Mediante la clase CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) y artículos relacionados., así como [Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## Requisitos  
 **encabezado:** afxsock.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)