---
title: CAsyncSocket (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c98703cbe68efc0ca7e40d3b25d0178d826855a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952611"
---
# <a name="casyncsocket-class"></a>CAsyncSocket (clase)
Representa un Socket de Windows, un extremo de comunicación de red.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAsyncSocket : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Construye un objeto `CAsyncSocket`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket:: Accept](#accept)|Acepta una conexión en el socket.|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|Notificación de eventos de solicitudes para el socket.|  
|[CAsyncSocket::Attach](#attach)|Asocia un identificador de socket a un `CAsyncSocket` objeto.|  
|[CAsyncSocket::Bind](#bind)|Asocia una dirección local del socket.|  
|[CAsyncSocket::Close](#close)|Cierra el socket.|  
|[CAsyncSocket:: Connect](#connect)|Establece una conexión a un socket del mismo nivel.|  
|[CAsyncSocket::Create](#create)|Crea un socket.|  
|[CAsyncSocket::Detach](#detach)|Desasocia un identificador de socket de un `CAsyncSocket` objeto.|  
|[CAsyncSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CAsyncSocket` objeto, dado un identificador de socket.|  
|[CAsyncSocket::GetLastError](#getlasterror)|Obtiene el estado de error para la última operación que no se pudo.|  
|[CAsyncSocket::GetPeerName](#getpeername)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket.|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtiene la dirección del socket del mismo nivel a la que el socket está conectados (identificadores de direcciones IPv6).|  
|[CAsyncSocket::GetSockName](#getsockname)|Obtiene el nombre local para un socket.|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtiene el nombre local para un socket (identificadores de direcciones IPv6).|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|Recupera una opción de socket.|  
|[CAsyncSocket::IOCtl](#ioctl)|Controla el modo del socket.|  
|[CAsyncSocket:: Listen](#listen)|Establece un socket para escuchar las solicitudes de conexión entrantes.|  
|[CAsyncSocket::Receive](#receive)|Recibe los datos desde el socket.|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Recibe un datagrama y almacena la dirección de origen.|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Recibe un datagrama y almacena la dirección de origen (identificadores de direcciones IPv6).|  
|[CAsyncSocket::Send](#send)|Envía datos a un socket conectado.|  
|[:: SendTo](#sendto)|Envía datos a un destino concreto.|  
|[CAsyncSocket::SendToEx](#sendtoex)|Envía datos a un destino concreto (identificadores de direcciones IPv6).|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|Establece una opción de socket.|  
|[CAsyncSocket::ShutDown](#shutdown)|Deshabilita `Send` o `Receive` llama en el socket.|  
|[CASyncSocket::Socket](#socket)|Asigna un identificador de socket.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|Notifica a un socket de escucha que puede aceptar solicitudes de conexión pendientes mediante una llamada a `Accept`.|  
|[CAsyncSocket::OnClose](#onclose)|Notifica a cerró un socket que el socket conectado a él.|  
|[CAsyncSocket::OnConnect](#onconnect)|Notifica a un socket de conexión que el intento de conexión está completo, si correctamente o con errores.|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Notifica a un socket de recepción que no hay datos de fuera de banda que deben leerse en el socket, normalmente un mensaje urgente.|  
|[CAsyncSocket::OnReceive](#onreceive)|Notifica a un socket de escucha que no hay datos para ser recuperado por una llamada a `Receive`.|  
|[CAsyncSocket::OnSend](#onsend)|Notifica a un socket que se pueden enviar datos mediante una llamada a `Send`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|Asigna un nuevo valor a un `CAsyncSocket` objeto.|  
|[CAsyncSocket::operator SOCKET](#operator_socket)|Utilice este operador para recuperar el **SOCKET** identificador de la `CAsyncSocket` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indica el **SOCKET** identificador asociado a este `CAsyncSocket` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Clase `CAsyncSocket` encapsula la API de funciones de Socket de Windows, proporcionar una abstracción orientada a objetos para los programadores que deseen utilizar Windows Sockets en conjunción con MFC.  
  
 Esta clase se basa en la suposición de que comprende las comunicaciones de red. Usted es responsable de controlar el bloqueo, las diferencias de orden de bytes, y las conversiones entre caracteres multibyte y Unicode establezca cadenas (MBCS). Si desea que una interfaz más adecuada que administra estos problemas en su nombre, vea la clase [CSocket](../../mfc/reference/csocket-class.md).  
  
 Para usar un `CAsyncSocket` objeto, llame a su constructor, a continuación, llamar a la [crear](#create) función para crear el identificador de socket subyacente (tipo `SOCKET`), excepto en sockets aceptados. Para realizar una llamada de socket de servidor el [escuchar](#listen) función miembro y para realizar una llamada de socket de cliente la [conectar](#connect) función miembro. El socket de servidor debe llamar a la [Accept](#accept) función al recibir una solicitud de conexión. Use el resto `CAsyncSocket` funciones para llevar a cabo las comunicaciones entre los sockets. Al finalizar, destruir la `CAsyncSocket` objeto si se ha creado en el montón; el destructor llama automáticamente a la [cerrar](#close) función. El **SOCKET** tipo de datos se describe en el artículo [Windows Sockets: fondo](../../mfc/windows-sockets-background.md).  
  
> [!NOTE]
>  Al utilizar sockets de MFC en subprocesos secundarios en una aplicación MFC vinculado estáticamente, se debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se denomina solo en el subproceso principal.  
  
 Para obtener más información, consulte [Windows Sockets: usar clase CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) y artículos relacionados., así como [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsock.h  
  
##  <a name="accept"></a>  CAsyncSocket:: Accept  
 Llame a esta función miembro para aceptar una conexión en un socket.  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *rConnectedSocket*  
 Una referencia identifica un nuevo socket que está disponible para la conexión.  
  
 *lpSockAddr*  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que recibe la dirección de la conexión de socket, tal y como se conoce en la red. El formato exacto de la *lpSockAddr* argumento viene determinado por la familia de direcciones que se establece cuando se creó el socket. Si *lpSockAddr* o *lpSockAddrLen* son iguales a **NULL**, a continuación, no se devuelve ninguna información sobre la dirección remota del socket aceptado.  
  
 *lpSockAddrLen*  
 Un puntero a la longitud de la dirección en *lpSockAddr* en bytes. El *lpSockAddrLen* es un parámetro de resultado del valor: debe contener inicialmente la cantidad de espacio que señala *lpSockAddr*; una vez devuelta contendrá la longitud real (en bytes) de la dirección devuelta.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento es demasiado pequeño (menor que el tamaño de un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINPROGRESS** una llamada de bloqueo de Windows Sockets está en curso.  
  
- **WSAEINVAL** `Listen` no fue invocado antes de Aceptar.  
  
- **WSAEMFILE** la cola está vacía en la entrada que se va a Aceptar y no hay ningún descriptores disponibles.  
  
- **WSAENOBUFS** ningún espacio de búfer está disponible.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP** el socket que se hace referencia no es un tipo que admita servicios orientados a conexiones.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y no hay ninguna conexión está presente para que se acepte.  
  
### <a name="remarks"></a>Comentarios  
 Esta rutina extrae la primera conexión de la cola de conexiones pendientes, se crea un nuevo socket con las mismas propiedades que este socket y se adjunta al *rConnectedSocket*. Si no hay ninguna conexión pendiente está presente en la cola, `Accept` devuelve cero y `GetLastError` devuelve un error. El socket aceptado ( *rConnectedSocket)* no se puede usar para aceptar más conexiones. El socket original permanece abierta y escucha.  
  
 El argumento *lpSockAddr* es un parámetro de resultado que se rellena con la dirección del socket de conexión, tal y como se sabe que el nivel de comunicaciones. `Accept` se utiliza con tipos de socket basado en conexión como **SOCK_STREAM**.  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 Llame a esta función miembro para solicitar la notificación de eventos para un socket.  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lEvent*  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- **FD_READ** desea recibir una notificación de preparación para la lectura.  
  
- **FD_WRITE** desea recibir una notificación cuando los datos están disponibles para su lectura.  
  
- **FD_OOB** desea recibir una notificación de la llegada de datos fuera de banda.  
  
- **FD_ACCEPT** desea recibir una notificación de las conexiones entrantes.  
  
- **FD_CONNECT** desea recibir una notificación de los resultados de la conexión.  
  
- **FD_CLOSE** desea recibir una notificación cuando se cerró un socket de un nodo del mismo nivel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEINVAL** indica que uno de los parámetros especificados no era válido.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para especificar qué funciones de notificación de devolución de llamada MFC se llamará para el socket. `AsyncSelect` se establece automáticamente este socket en modo de no bloqueo. Para obtener más información, vea el artículo [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 Llame a esta función miembro para adjuntar el *hSocket* identificador de un `CAsyncSocket` objeto.  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *hSocket*  
 Contiene un identificador de un socket.  
  
 *lEvent*  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- **FD_READ** desea recibir una notificación de preparación para la lectura.  
  
- **FD_WRITE** desea recibir una notificación cuando los datos están disponibles para su lectura.  
  
- **FD_OOB** desea recibir una notificación de la llegada de datos fuera de banda.  
  
- **FD_ACCEPT** desea recibir una notificación de las conexiones entrantes.  
  
- **FD_CONNECT** desea recibir una notificación de los resultados de la conexión.  
  
- **FD_CLOSE** desea recibir una notificación cuando se cerró un socket de un nodo del mismo nivel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 El **SOCKET** identificador se almacena en el objeto [m_hSocket](#m_hsocket) miembro de datos.  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 Llame a esta función miembro para asociar una dirección local del socket.  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parámetros  
 *nSocketPort*  
 El puerto identifica la aplicación de socket.  
  
 *lpszSocketAddress*  
 La dirección de red, un número separado por puntos, como "128.56.22.8". Pasar el **NULL** de cadena para este parámetro indica la `CAsyncSocket` instancia debe escuchar la actividad del cliente en todas las interfaces de red.  
  
 *lpSockAddr*  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección que se asigna a este socket.  
  
 *nSockAddrLen*  
 La longitud de la dirección en *lpSockAddr* en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEADDRINUSE** la dirección especificada ya está en uso. (Consulte la **SO_REUSEADDR** opción situada debajo de socket [SetSockOpt](#setsockopt).)  
  
- **WSAEFAULT** el *nSockAddrLen* argumento es demasiado pequeño (menor que el tamaño de un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINPROGRESS** una llamada de bloqueo de Windows Sockets está en curso.  
  
- **WSAEAFNOSUPPORT** la familia de direcciones especificado no es compatible con este puerto.  
  
- **WSAEINVAL** el socket ya está enlazado a una dirección.  
  
- **WSAENOBUFS** no hay suficientes búferes disponibles, si hay demasiadas conexiones.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Esta rutina se utiliza en un datagrama no conectada o un socket de secuencia, que antes posteriores `Connect` o `Listen` llamadas. Antes de pueda aceptar solicitudes de conexión, un socket de servidor escucha debe seleccionar un número de puerto y que sea conocido de Windows Sockets mediante una llamada a `Bind`. `Bind` establece la asociación local (número de dirección/puerto de host) del socket asignando un nombre local para un socket sin nombre.  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 Construye un objeto de socket en blanco.  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, se debe llamar a su `Create` función de miembro para crear el **SOCKET** de la estructura de datos y enlazar su dirección. (En el servidor de una comunicación de Windows Sockets, cuando el socket de escucha crea un socket para usar en el `Accept` llamada, no se llama `Create` para ese socket.)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 Cierra el socket.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función libera el descriptor de socket para que aún más las referencias a él se producirá un error con el error **WSAENOTSOCK**. Si se trata de la última referencia al socket subyacente, la información de asignación de nombres asociada y los datos en cola se descartan. Llamadas de destructor del objeto de socket `Close` para usted.  
  
 Para `CAsyncSocket`, pero no para `CSocket`, la semántica de `Close` se ven afectadas por las opciones de socket **SO_LINGER** y **SO_DONTLINGER**. Para obtener más información, vea la función miembro `GetSockOpt`.  
  
##  <a name="connect"></a>  CAsyncSocket:: Connect  
 Llame a esta función miembro para establecer una conexión con una secuencia no conectada o un socket de datagrama.  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszHostAddress*  
 La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número separado por puntos, como "128.56.22.8".  
  
 *nHostPort*  
 El puerto identifica la aplicación de socket.  
  
 *lpSockAddr*  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección del socket conectado.  
  
 *nSockAddrLen*  
 La longitud de la dirección en *lpSockAddr* en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Si indica un código de error **WSAEWOULDBLOCK**y la aplicación utiliza las devoluciones de llamada reemplazables, su aplicación recibirá un `OnConnect` mensaje una vez completada la operación de conexión. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEADDRINUSE** la dirección especificada ya está en uso.  
  
- **WSAEINPROGRESS** una llamada de bloqueo de Windows Sockets está en curso.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAECONNREFUSED** se rechazó el intento de conexión.  
  
- **WSAEDESTADDRREQ** se necesita una dirección de destino.  
  
- **WSAEFAULT** el *nSockAddrLen* argumento sea incorrecto.  
  
- **WSAEINVAL** dirección de host no válido.  
  
- **WSAEISCONN** el socket ya está conectado.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
- **WSAENOBUFS** ningún espacio de búfer está disponible. No se puede conectar el socket.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAETIMEDOUT** intentan conectarse agotó sin necesidad de establecer una conexión.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y no se puede completar la conexión inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 Si el socket no está enlazado, valores únicos se asignan a la asociación local por el sistema y el socket se marca como dependiente. Tenga en cuenta que si el campo de dirección de la estructura de nombre es todo ceros, `Connect` devolverá cero. Para obtener información de error extendida, llame a la `GetLastError` función miembro.  
  
 Para los sockets de secuencia (tipo **SOCK_STREAM**), se inicia una conexión activa al host externo. Cuando se complete correctamente la llamada de socket, el socket está listo para enviar y recibir datos.  
  
 Para un socket de datagrama (tipo **SOCK_DGRAM**), se establece un destino de forma predeterminada, que se usará en posteriores `Send` y `Receive` llamadas.  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 Llame a la `Create` función miembro después de crear un objeto de socket para crear el socket de Windows y adjúntela.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *nSocketPort*  
 Un puerto conocido para su uso con el socket, o 0 si desea que Windows Sockets para seleccionar un puerto.  
  
 *nSocketType*  
 **SOCK_STREAM** o **SOCK_DGRAM**.  
  
 *lEvent*  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- **FD_READ** desea recibir una notificación de preparación para la lectura.  
  
- **FD_WRITE** desea recibir una notificación de preparación para escribir en él.  
  
- **FD_OOB** desea recibir una notificación de la llegada de datos fuera de banda.  
  
- **FD_ACCEPT** desea recibir una notificación de las conexiones entrantes.  
  
- **FD_CONNECT** desea recibir una notificación de conexión completada.  
  
- **FD_CLOSE** desea recibir una notificación de cierre del socket.  
  
 *lpszSockAddress*  
 Un puntero a una cadena que contiene la dirección de red del socket conectado, un número separado por puntos, como "128.56.22.8". Pasar el **NULL** de cadena para este parámetro indica la **CAsyncSocket** instancia debe escuchar la actividad del cliente en todas las interfaces de red.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEAFNOSUPPORT** no se admite la familia de direcciones especificado.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- **WSAENOBUFS** ningún espacio de búfer está disponible. No se puede crear el socket.  
  
- **WSAEPROTONOSUPPORT** no se admite el puerto especificado.  
  
- **WSAEPROTOTYPE** el puerto especificado es del tipo incorrecto para este socket.  
  
- **WSAESOCKTNOSUPPORT** el tipo de socket especificado no se admite en esta familia de direcciones.  
  
### <a name="remarks"></a>Comentarios  
 `Create` llamadas [Socket](#socket) y si se realiza correctamente, llama a [enlazar](#bind) para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:  
  
- **SOCK_STREAM** proporciona secuenciado, secuencias de bytes confiable, dúplex completo, según la conexión. Usa el protocolo de Control de transmisión (TCP) para la familia de direcciones de Internet.  
  
- **SOCK_DGRAM** admite datagramas, que son paquetes sin conexión no confiables de longitud máxima fija (normalmente corta). Usa el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet.  
  
    > [!NOTE]
    >  El `Accept` función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Se debe crear este objeto antes de llamar a `Accept`. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. No llame a `Create` para este nuevo objeto de socket.  
  
> [!IMPORTANT]
> `Create` es **no** segura para subprocesos.  Si se llama en un entorno multiproceso donde se puede invocar simultáneamente en subprocesos diferentes, asegúrese de proteger cada llamada con una exclusión mutua u otro bloqueo de sincronización.  
  
 Para obtener más información acerca de los sockets de secuencia y datagrama, vea los artículos [Windows Sockets: fondo](../../mfc/windows-sockets-background.md) y [Windows Sockets: puertos y direcciones de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md) y [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 Llame a esta función miembro para separar el **SOCKET** controlar en el *m_hSocket* miembro de datos de la `CAsyncSocket` de objeto y establecer *m_hSocket* a **NULL** .  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 Devuelve un puntero a un `CAsyncSocket` objeto.  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parámetros  
 *hSocket*  
 Contiene un identificador de un socket.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CAsyncSocket` objeto, o **NULL** si no hay ningún `CAsyncSocket` objeto asociado al *hSocket*.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se especifica un **SOCKET** controlar si una `CAsyncSocket` objeto no está asociado al identificador, la función miembro devuelve **NULL**.  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 Llame a esta función miembro para obtener el estado de error de la última operación que no se pudo.  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto indica el código de error de la rutina de API de Windows Sockets última realizada por este subproceso.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una función miembro determinada indica que se ha producido un error, `GetLastError` debe llamarse para recuperar el código de error adecuado. Vea las descripciones de la función miembro individual para obtener una lista de códigos de error es aplicable.  
  
 Para obtener más información acerca de los códigos de error, consulte [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 Llame a esta función miembro para obtener la dirección del socket del mismo nivel a la que se conecta este socket.  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parámetros  
 *rPeerAddress*  
 Referencia a un `CString` objeto que recibe una dirección IP numérica con puntos.  
  
 *rPeerPort*  
 Referencia a un **UINT** que almacena un puerto.  
  
 *lpSockAddr*  
 Un puntero a la [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que recibe el nombre del socket del mismo nivel.  
  
 *lpSockAddrLen*  
 Un puntero a la longitud de la dirección en *lpSockAddr* en bytes. Una vez devuelta, el *lpSockAddrLen* argumento contiene el tamaño real de *lpSockAddr* devuelto en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento no es lo suficientemente grande.  
  
- **WSAEINPROGRESS** una llamada de bloqueo de Windows Sockets está en curso.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Para controlar las direcciones IPv6, use [CAsyncSocket::GetPeerNameEx](#getpeernameex).  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 Llame a esta función miembro para obtener la dirección del socket del mismo nivel a la que este socket está conectados (identificadores de direcciones IPv6).  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>Parámetros  
 *rPeerAddress*  
 Referencia a un `CString` objeto que recibe una dirección IP numérica con puntos.  
  
 *rPeerPort*  
 Referencia a un **UINT** que almacena un puerto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento no es lo suficientemente grande.  
  
- **WSAEINPROGRESS** una llamada de bloqueo de Windows Sockets está en curso.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es el mismo que [CAsyncSocket::GetPeerName](#getpeername) salvo que es capaz de abrir IPv6 protocolos anteriores, así como las direcciones.  
  
##  <a name="getsockname"></a>  CAsyncSocket::GetSockName  
 Llame a esta función miembro para obtener el nombre local de un socket.  
  
```  
BOOL GetSockName(
    CString& rSocketAddress,  
    UINT& rSocketPort);

 
BOOL GetSockName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parámetros  
 *rSocketAddress*  
 Referencia a un `CString` objeto que recibe una dirección IP numérica con puntos.  
  
 *rSocketPort*  
 Referencia a un **UINT** que almacena un puerto.  
  
 *lpSockAddr*  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que recibe la dirección del socket.  
  
 *lpSockAddrLen*  
 Un puntero a la longitud de la dirección en *lpSockAddr* en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento no es lo suficientemente grande.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEINVAL** el socket no se ha enlazado a una dirección con `Bind`.  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada es especialmente útil cuando un `Connect` llamada se ha realizado sin hacerlo un `Bind` primero; esta llamada proporciona el único medio por el que se puede determinar la asociación local que se ha establecido por el sistema.  
  
 Para controlar las direcciones IPv6, use [CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 Llame a esta función miembro para obtener el nombre local de un socket (identificadores de direcciones IPv6).  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>Parámetros  
 *rSocketAddress*  
 Referencia a un `CString` objeto que recibe una dirección IP numérica con puntos.  
  
 *rSocketPort*  
 Referencia a un **UINT** que almacena un puerto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento no es lo suficientemente grande.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEINVAL** el socket no se ha enlazado a una dirección con `Bind`.  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada es el mismo que [CAsyncSocket::GetSockName](#getsockname) salvo que es capaz de abrir IPv6 protocolos anteriores, así como las direcciones.  
  
 Esta llamada es especialmente útil cuando un `Connect` llamada se ha realizado sin hacerlo un `Bind` primero; esta llamada proporciona el único medio por el que se puede determinar la asociación local que se ha establecido por el sistema.  
  
##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt  
 Llame a esta función miembro para recuperar una opción de socket.  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parámetros  
 *nOptionName*  
 La opción de socket para los que es el valor va a recuperar.  
  
 *lpOptionValue*  
 Un puntero al búfer en el que el valor de la opción solicitada es va a devolver. Se devuelve el valor asociado a la opción seleccionada en el búfer *lpOptionValue*. El entero que señala *lpOptionLen* originalmente debe contener el tamaño de este búfer en bytes; y en la devolución, se establecerá en el tamaño del valor devuelto. Para **SO_LINGER**, será el tamaño de un `LINGER` estructura; para todas las demás opciones será el tamaño de un **BOOL** o un **int**, en función de la opción. Ver la lista de opciones y sus tamaños en la sección Comentarios.  
  
 *lpOptionLen*  
 Un puntero al tamaño de la *lpOptionValue* búfer en bytes.  
  
 *nLevel*  
 El nivel en el que se define la opción; los niveles admitidos solo son **SOL_SOCKET** y **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Si nunca se ha establecido una opción con `SetSockOpt`, a continuación, `GetSockOpt` devuelve el valor predeterminado para la opción. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpOptionLen* argumento no era válido.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAENOPROTOOPT** la opción es desconocido o no es compatible. En concreto, **SO_BROADCAST** no se admite en sockets de tipo **SOCK_STREAM**, mientras que **SO_ACCEPTCONN**, **SO_DONTLINGER**,  **SO_KEEPALIVE**, **SO_LINGER**, y **SO_OOBINLINE** no se admite en sockets de tipo **SOCK_DGRAM**.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 `GetSockOpt` Recupera el valor actual de una opción de socket asociado con un socket de cualquier tipo, en cualquier estado y almacena el resultado en *lpOptionValue*. Opciones afectan a las operaciones de socket, como el enrutamiento de paquetes, transferencia de datos fuera de banda y así sucesivamente.  
  
 Se admiten las siguientes opciones para `GetSockOpt`. El tipo identifica el tipo de datos dirigidos por *lpOptionValue*. El **TCP_NODELAY** opción utiliza nivel **IPPROTO_TCP**; todas las demás opciones utilizan nivel **SOL_SOCKET**.  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Socket está escuchando.|  
|**SO_BROADCAST**|**BOOL**|Socket está configurado para la transmisión de mensajes de difusión.|  
|**SO_DEBUG**|**BOOL**|Está habilitada la depuración.|  
|**SO_DONTLINGER**|**BOOL**|Si es true, el **SO_LINGER** opción está deshabilitada.|  
|**SO_DONTROUTE**|**BOOL**|El enrutamiento está deshabilitado.|  
|**SO_ERROR**|**int**|Recuperar el estado de error y borrar.|  
|**SO_KEEPALIVE**|**BOOL**|Se envían comandos keepalive.|  
|**SO_LINGER**|**struct PERMANENCIA**|Devuelve las opciones actuales de permanencia.|  
|**SO_OOBINLINE**|**BOOL**|Recibe datos fuera de banda en el flujo de datos normal.|  
|**SO_RCVBUF**|**int**|Recibe el tamaño del búfer de.|  
|**SO_REUSEADDR**|**BOOL**|El socket se puede enlazar a una dirección que ya está en uso.|  
|**SO_SNDBUF**|**int**|Tamaño de búfer para envía.|  
|**SO_TYPE**|**int**|El tipo de socket (por ejemplo, **SOCK_STREAM**).|  
|**TCP_NODELAY**|**BOOL**|Deshabilita el algoritmo de Nagle para la fusión de envíos.|  
  
 Opciones de Berkeley Software Distribution (BSD) no se admite para `GetSockOpt` son:  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|**int**|Recibir marca de agua suave.|  
|**SO_RCVTIMEO**|**int**|Tiempo de espera de recepción.|  
|**SO_SNDLOWAT**|**int**|Enviar la marca de agua suave.|  
|**SO_SNDTIMEO**|**int**|Tiempo de espera de envío.|  
|**IP_OPTIONS**||Obtener opciones de encabezado IP.|  
|**TCP_MAXSEG**|**int**|Obtener el tamaño máximo de segmento TCP.|  
  
 Al llamar a `GetSockOpt` con una opción no admitida se producirá en el código de error **WSAENOPROTOOPT** que se devuelven desde `GetLastError`.  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 Llame a esta función miembro para controlar el modo de un socket.  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>Parámetros  
 *lCommand*  
 El comando para llevar a cabo en el socket.  
  
 *lpArgument*  
 Un puntero a un parámetro para *lCommand*.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEINVAL** *lCommand* no es un comando válido, o *lpArgument* no es un parámetro aceptable para *lCommand*, o el comando no es aplicable a las tipo de socket proporcionado.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Esta rutina se puede usar en cualquier socket en cualquier estado. Sirve para obtener o recuperar los parámetros operativos asociadas al socket, independiente del subsistema de protocolo y las comunicaciones. Se admiten los siguientes comandos:  
  
- **FIONBIO** habilitar o deshabilitar el modo de no bloqueo en el socket. El *lpArgument* parámetro señala a una `DWORD`, que es distinto de cero si es el modo de no bloqueo esté habilitado y cero si tiene que estar deshabilitado. Si `AsyncSelect` se ha emitido en un socket, a continuación, cualquier intento de usar `IOCtl` volver a establecer el socket en modo de bloqueo se producirá un error con **WSAEINVAL**. Para establecer el socket volver al modo de bloqueo y evitar el **WSAEINVAL** error, primero debe deshabilitar una aplicación `AsyncSelect` mediante una llamada a `AsyncSelect` con el *lEvent* parámetro igual a 0, a continuación, llamar `IOCtl`.  
  
- **FIONREAD** determinar el número máximo de bytes que se pueden leer con una `Receive` llamar desde este socket. El *lpArgument* parámetro señala a una `DWORD` en el que `IOCtl` almacena el resultado. Si este socket es de tipo **SOCK_STREAM**, **FIONREAD** devuelve la cantidad total de datos que pueden leerse en una sola `Receive`; esto es normalmente el mismo que la cantidad total de datos en cola en el socket. Si este socket es de tipo **SOCK_DGRAM**, **FIONREAD** devuelve el tamaño del primer datagrama en cola en el socket.  
  
- **SIOCATMARK** determinar si se han leído todos los datos de fuera de banda. Esto se aplica solo a un socket de tipo **SOCK_STREAM** que se ha configurado para la recepción en línea de todos los datos fuera de banda ( **SO_OOBINLINE**). Si no hay datos fuera de banda está esperando que debe leerse, la operación devuelve es distinto de cero. De lo contrario devuelve 0 y el siguiente `Receive` o `ReceiveFrom` realizadas en el socket recuperará algunos o todos los datos anterior a la "marca"; la aplicación debe utilizar el **SIOCATMARK** operación para determinar si alguno los datos permanecen. Si no hay ningún dato normal antes de los datos (fuera de banda) "urgentes", se recibirán en orden. (Tenga en cuenta que un `Receive` o `ReceiveFrom` nunca se combinen los datos de fuera de banda y normales en la misma llamada.) El *lpArgument* parámetro señala a una `DWORD` en el que `IOCtl` almacena el resultado.  
  
 Esta función es un subconjunto de `ioctl()` de sockets Berkeley. En concreto, no hay ningún comando que es equivalente a **FIOASYNC**, mientras que **SIOCATMARK** es el comando solo de nivel de socket que se admite.  
  
##  <a name="listen"></a>  CAsyncSocket:: Listen  
 Llame a esta función miembro para realizar escuchas de solicitudes de conexión entrantes.  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>Parámetros  
 *nConnectionBacklog*  
 La longitud máxima que puede alcanzar la cola de conexiones pendientes. Intervalo válido es de 1 a 5.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEADDRINUSE** se ha realizado un intento para escuchar en una dirección está en uso.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEINVAL** el socket no se ha enlazado con `Bind` o ya está conectado.  
  
- **WSAEISCONN** el socket ya está conectado.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- **WSAENOBUFS** ningún espacio de búfer está disponible.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP** el socket que se hace referencia no es de un tipo que admita la `Listen` operación.  
  
### <a name="remarks"></a>Comentarios  
 Para aceptar conexiones, el socket se crea por primera vez con `Create`, se especifica un trabajo pendiente para las conexiones entrantes con `Listen`, y, a continuación, se aceptan las conexiones con `Accept`. `Listen` solo se aplica a sockets que admiten conexiones, es decir, los de tipo **SOCK_STREAM**. Este socket se pone en modo "pasivo" que haya confirmado ni puestos en cola pendientes de aceptación por el proceso de las conexiones entrantes.  
  
 Esta función se utiliza normalmente por servidores (o cualquier aplicación que desea aceptar conexiones) que puede tener más de una solicitud de conexión a la vez: si llega una solicitud de conexión con la cola completa, el cliente recibirá un error con una indicación de  **WSAECONNREFUSED**.  
  
 `Listen` intenta continuar funcionando racional cuando no hay ningún puerto disponible (descriptores). Va a aceptar conexiones hasta que la cola se vacía. Si los puertos estén disponibles, una llamada posterior a `Listen` o `Accept` se rellene la cola para el actual o el más reciente "trabajo pendiente," si es posible y reanudar escuchar las conexiones entrantes.  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 Contiene el **SOCKET** controlar para el socket encapsulado por este `CAsyncSocket` objeto.  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 Lo llama el marco para notificar a un socket de escucha que puede aceptar solicitudes de conexión pendientes mediante una llamada a la [Accept](#accept) función miembro.  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nErrorCode*  
 El error más reciente en un socket. Los siguientes códigos de error se aplica a la `OnAccept` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 Lo llama el marco de trabajo para notificar a este socket que se cierra el socket conectado por su proceso.  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nErrorCode*  
 El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnClose` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAECONNRESET** se ha restablecido la conexión en el lado remoto.  
  
- **WSAECONNABORTED** se anuló la conexión debido a tiempo de espera u otro error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 Lo llama el marco de trabajo para notificar a conectar el socket que su intento de conexión se ha completado, ya sea correctamente o error.  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nErrorCode*  
 El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnConnect` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAEADDRINUSE** la dirección especificada ya está en uso.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAECONNREFUSED** el intento de conexión se rechazó con fuerza.  
  
- **WSAEDESTADDRREQ** se necesita una dirección de destino.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento sea incorrecto.  
  
- **WSAEINVAL** el socket ya está enlazado a una dirección.  
  
- **WSAEISCONN** el socket ya está conectado.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
- **WSAENOBUFS** ningún espacio de búfer está disponible. No se puede conectar el socket.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor es un archivo, no es un socket.  
  
- **WSAETIMEDOUT** el intento de conexión agotó el tiempo de espera sin establecer una conexión.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En [CSocket](../../mfc/reference/csocket-class.md), el `OnConnect` nunca se llama la función de notificación. Para las conexiones, basta con llamar a `Connect`, que se devolverá cuando se complete la conexión (éxito o error). Cómo se administran las notificaciones de conexión es un detalle de implementación de MFC.  
  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 Lo llama el marco de trabajo para notificar al socket receptor que el socket emisor tiene datos fuera de banda para enviar.  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nErrorCode*  
 El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnOutOfBandData` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
### <a name="remarks"></a>Comentarios  
 Datos de fuera de banda son un canal lógicamente independiente que está asociado a cada par de sockets conectados de tipo **SOCK_STREAM**. El canal se utiliza generalmente para enviar datos urgentes.  
  
 MFC admite datos fuera de banda, pero los usuarios de la clase `CAsyncSocket` no se recomienda utilizarla. La manera más fácil es crear un segundo socket para pasar estos datos. Para obtener más información acerca de los datos fuera de banda, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 Lo llama el marco para notificar a este socket que hay datos en el búfer que se pueden recuperar mediante una llamada a la `Receive` función miembro.  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nErrorCode*  
 El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnReceive` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 Lo llama el marco para notificar el socket que ahora se pueden enviar datos mediante una llamada a la **enviar** función miembro.  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nErrorCode*  
 El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnSend` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 Asigna un nuevo valor a un `CAsyncSocket` objeto.  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *rSrc*  
 Una referencia a un archivo `CAsyncSocket` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para copiar uno existente `CAsyncSocket` objeto a otro `CAsyncSocket` objeto.  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator SOCKET  
 Utilice este operador para recuperar el **SOCKET** identificador de la `CAsyncSocket` objeto.  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador de la **SOCKET** objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar el identificador para llamar directamente a las API de Windows.  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 Llame a esta función miembro para recibir datos de un socket.  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un búfer para los datos entrantes.  
  
 *nBufLen*  
 La longitud de *lpBuf* en bytes.  
  
 *nFlags*  
 Especifica la manera en que se realiza la llamada. La semántica de esta función está determinada por las opciones de socket y *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:  
  
- **MSG_PEEK** consultar los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.  
  
- **MSG_OOB** procesar los datos fuera de banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `Receive` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. En caso contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `Receive` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 0 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la `Receive` operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.  
  
- **WSAEINVAL** el socket no se ha enlazado con `Bind`.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido a tiempo de espera u otro error.  
  
- **WSAECONNRESET** se restableció el circuito virtual en el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para secuencias conectados o sockets de datagramas y se utiliza para leer los datos entrantes.  
  
 Para los sockets de tipo **SOCK_STREAM**, tal y como se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si se ha configurado el socket para la recepción en línea de datos fuera de banda (opción de socket **SO_OOBINLINE**) y no se ha leído los datos fuera de banda, se devolverán datos solo fuera de banda. La aplicación puede utilizar el **IOCtlSIOCATMARK** opción o [OnOutOfBandData](#onoutofbanddata) para determinar si sigue habiendo datos más fuera de banda que debe leerse.  
  
 Para los sockets de datagramas, se extraen los datos desde el primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del datagrama, el exceso de datos se pierde, y `Receive` devuelve un valor de **SOCKET_ERROR** con el código de error establecido en  **WSAEMSGSIZE**. Si no hay datos entrantes están disponibles en el socket, un valor de **SOCKET_ERROR** se devuelve con el código de error establecido en **WSAEWOULDBLOCK**. El [OnReceive](#onreceive) función de devolución de llamada puede utilizarse para determinar cuándo llegan a más datos.  
  
 Si el socket es de tipo **SOCK_STREAM** y el lado remoto cerró la conexión correctamente, un `Receive` finalizará inmediatamente con 0 bytes recibidos. Si se ha restablecido la conexión, un `Receive` se producirá un error con el error **WSAECONNRESET**.  
  
 `Receive` se debe llamar una sola vez para cada vez que [CAsyncSocket::OnReceive](#onreceive) se llama.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en el [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura o en *rSocketAddress*.  
  
```  
int ReceiveFrom(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);

 
int ReceiveFrom(
    void* lpBuf,  
    int nBufLen,  
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un búfer para los datos entrantes.  
  
 *nBufLen*  
 La longitud de *lpBuf* en bytes.  
  
 *rSocketAddress*  
 Referencia a un `CString` objeto que recibe una dirección IP numérica con puntos.  
  
 *rSocketPort*  
 Referencia a un **UINT** que almacena un puerto.  
  
 *lpSockAddr*  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección de origen cuando se devuelve.  
  
 *lpSockAddrLen*  
 Un puntero a la longitud de la dirección de origen *lpSockAddr* en bytes.  
  
 *nFlags*  
 Especifica la manera en que se realiza la llamada. La semántica de esta función está determinada por las opciones de socket y *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:  
  
- **MSG_PEEK** consultar los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.  
  
- **MSG_OOB** procesar los datos fuera de banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `ReceiveFrom` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. En caso contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a `GetLastError`. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento no era válido: el *lpSockAddr* búfer era demasiado pequeño para dar cabida a la dirección del mismo nivel.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEINVAL** el socket no se ha enlazado con `Bind`.  
  
- **WSAENOTCONN** el socket no está conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `ReceiveFrom` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 0 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la `ReceiveFrom` operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido a tiempo de espera u otro error.  
  
- **WSAECONNRESET** se restableció el circuito virtual en el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.  
  
 Para controlar las direcciones IPv6, use [CAsyncSocket::ReceiveFromEx](#receivefromex).  
  
 Para los sockets de tipo **SOCK_STREAM**, tal y como se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si se ha configurado el socket para la recepción en línea de datos fuera de banda (opción de socket **SO_OOBINLINE**) y no se ha leído los datos fuera de banda, se devolverán datos solo fuera de banda. La aplicación puede utilizar el **IOCtlSIOCATMARK** opción o `OnOutOfBandData` para determinar si sigue habiendo datos más fuera de banda que debe leerse. El *lpSockAddr* y *lpSockAddrLen* se omiten los parámetros de **SOCK_STREAM** sockets.  
  
 Para los sockets de datagramas, se extraen los datos desde el primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del mensaje, el exceso de datos se pierde, y `ReceiveFrom` devuelve un valor de **SOCKET_ERROR** con el código de error establecido en  **WSAEMSGSIZE**.  
  
 Si *lpSockAddr* es distinto de cero, y el socket es de tipo **SOCK_DGRAM**, la dirección de red del socket que envió los datos se copia en la correspondiente [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura. El valor que señala *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modifica en el valor devuelto para indicar el tamaño real de la dirección que se almacenan allí. Si no hay datos entrantes están disponibles en el socket, el `ReceiveFrom` llamada espera los datos a que llegue a menos que sea el socket no sea de bloqueo. En este caso, un valor de **SOCKET_ERROR** se devuelve con el código de error establecido en **WSAEWOULDBLOCK**. El `OnReceive` devolución de llamada puede usarse para determinar cuándo llegan a más datos.  
  
 Si el socket es de tipo **SOCK_STREAM** y el lado remoto cerró la conexión correctamente, un `ReceiveFrom` finalizará inmediatamente con 0 bytes recibidos.  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en el [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura o en *rSocketAddress* (controla las direcciones IPv6).  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un búfer para los datos entrantes.  
  
 *nBufLen*  
 La longitud de *lpBuf* en bytes.  
  
 *rSocketAddress*  
 Referencia a un `CString` objeto que recibe una dirección IP numérica con puntos.  
  
 *rSocketPort*  
 Referencia a un **UINT** que almacena un puerto.  
  
 *nFlags*  
 Especifica la manera en que se realiza la llamada. La semántica de esta función está determinada por las opciones de socket y *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:  
  
- **MSG_PEEK** consultar los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.  
  
- **MSG_OOB** procesar los datos fuera de banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `ReceiveFromEx` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. En caso contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a `GetLastError`. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** el *lpSockAddrLen* argumento no era válido: el *lpSockAddr* búfer era demasiado pequeño para dar cabida a la dirección del mismo nivel.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEINVAL** el socket no se ha enlazado con `Bind`.  
  
- **WSAENOTCONN** el socket no está conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `ReceiveFromEx` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 0 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la `ReceiveFromEx` operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido a tiempo de espera u otro error.  
  
- **WSAECONNRESET** se restableció el circuito virtual en el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.  
  
 Esta función es el mismo que [CAsyncSocket::ReceiveFrom](#receivefrom) salvo que es capaz de abrir IPv6 protocolos anteriores, así como las direcciones.  
  
 Para los sockets de tipo **SOCK_STREAM**, tal y como se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si se ha configurado el socket para la recepción en línea de datos fuera de banda (opción de socket **SO_OOBINLINE**) y no se ha leído los datos fuera de banda, se devolverán datos solo fuera de banda. La aplicación puede utilizar el **IOCtlSIOCATMARK** opción o `OnOutOfBandData` para determinar si sigue habiendo datos más fuera de banda que debe leerse. El *lpSockAddr* y *lpSockAddrLen* se omiten los parámetros de **SOCK_STREAM** sockets.  
  
 Para los sockets de datagramas, se extraen los datos desde el primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del mensaje, el exceso de datos se pierde, y `ReceiveFromEx` devuelve un valor de **SOCKET_ERROR** con el código de error establecido en  **WSAEMSGSIZE**.  
  
 Si *lpSockAddr* es distinto de cero, y el socket es de tipo **SOCK_DGRAM**, la dirección de red del socket que envió los datos se copia en la correspondiente [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura. El valor que señala *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modifica en el valor devuelto para indicar el tamaño real de la dirección que se almacenan allí. Si no hay datos entrantes están disponibles en el socket, el `ReceiveFromEx` llamada espera los datos a que llegue a menos que sea el socket no sea de bloqueo. En este caso, un valor de **SOCKET_ERROR** se devuelve con el código de error establecido en **WSAEWOULDBLOCK**. El `OnReceive` devolución de llamada puede usarse para determinar cuándo llegan a más datos.  
  
 Si el socket es de tipo **SOCK_STREAM** y el lado remoto cerró la conexión correctamente, un `ReceiveFromEx` finalizará inmediatamente con 0 bytes recibidos.  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 Llame a esta función miembro para enviar datos de un socket conectado.  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un búfer que contiene los datos que se transmitan.  
  
 *nBufLen*  
 La longitud de los datos de *lpBuf* en bytes.  
  
 *nFlags*  
 Especifica la manera en que se realiza la llamada. La semántica de esta función está determinada por las opciones de socket y *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:  
  
- **MSG_DONTROUTE** especifica que los datos no deben estar sujeta a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.  
  
- **MSG_OOB** enviar datos fuera de banda ( **SOCK_STREAM** solo).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `Send` devuelve el número total de caracteres que se envían. (Tenga en cuenta que puede ser menor que el número indicado por *nBufLen*.) En caso contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEACCES** la dirección solicitada es una dirección de difusión, pero no se estableció el marcador adecuado.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEFAULT** el *lpBuf* el argumento no es una parte válida del espacio de direcciones del usuario.  
  
- **WSAENETRESET** se debe restablecer la conexión porque la implementación de Windows Sockets quitó.  
  
- **WSAENOBUFS** implementación de los Sockets de Windows notifica un interbloqueo de búfer.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `Send` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 1 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como sin bloqueo y bloqueará la operación solicitada.  
  
- **WSAEMSGSIZE** el socket es de tipo **SOCK_DGRAM**, y el datagrama es mayor que el límite máximo admitido por la implementación de Windows Sockets.  
  
- **WSAEINVAL** el socket no se ha enlazado con `Bind`.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido a tiempo de espera u otro error.  
  
- **WSAECONNRESET** se restableció el circuito virtual en el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 `Send` se usa para escribir los datos salientes en secuencia conectados o sockets de datagramas. Para los sockets de datagramas, se debe tener cuidado de no debe superar el tamaño máximo de paquetes IP de las subredes subyacentes, que viene dada por la **iMaxUdpDg** elemento en el [WSADATA](../../mfc/reference/wsadata-structure.md) estructura devuelta por `AfxSocketInit`. Si los datos son demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error **WSAEMSGSIZE** se devuelve a través de `GetLastError`, y se transmite ningún dato.  
  
 Tenga en cuenta que para un datagrama socket la finalización correcta de una `Send` no indica que los datos se ha entregado correctamente.  
  
 En `CAsyncSocket` objetos de tipo **SOCK_STREAM**, el número de bytes escritos puede estar entre 1 y la longitud solicitada, dependiendo de la disponibilidad de búfer en los hosts locales y externas.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAsyncSocket::OnSend](#onsend).  
  
##  <a name="sendto"></a>  :: SendTo  
 Llame a esta función miembro para enviar datos a un destino concreto.  
  
```  
int SendTo(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);

 
int SendTo(
    const void* lpBuf,  
    int nBufLen,  
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un búfer que contiene los datos que se transmitan.  
  
 *nBufLen*  
 La longitud de los datos de *lpBuf* en bytes.  
  
 *nHostPort*  
 El puerto identifica la aplicación de socket.  
  
 *lpszHostAddress*  
 La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número separado por puntos, como "128.56.22.8".  
  
 *nFlags*  
 Especifica la manera en que se realiza la llamada. La semántica de esta función está determinada por las opciones de socket y *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:  
  
- **MSG_DONTROUTE** especifica que los datos no deben estar sujeta a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.  
  
- **MSG_OOB** enviar datos fuera de banda ( **SOCK_STREAM** solo).  
  
 *lpSockAddr*  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección del socket de destino.  
  
 *nSockAddrLen*  
 La longitud de la dirección en *lpSockAddr* en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `SendTo` devuelve el número total de caracteres que se envían. (Tenga en cuenta que puede ser menor que el número indicado por *nBufLen*.) En caso contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEACCES** la dirección solicitada es una dirección de difusión, pero no se estableció el marcador adecuado.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEFAULT** el *lpBuf* o *lpSockAddr* parámetros no forman parte del espacio de direcciones del usuario, o la *lpSockAddr* argumento (menor que el tamaño es demasiado pequeño de un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINVAL** el nombre de host no es válido.  
  
- **WSAENETRESET** se debe restablecer la conexión porque la implementación de Windows Sockets quitó.  
  
- **WSAENOBUFS** implementación de los Sockets de Windows notifica un interbloqueo de búfer.  
  
- **WSAENOTCONN** el socket no está conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `SendTo` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 1 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como sin bloqueo y bloqueará la operación solicitada.  
  
- **WSAEMSGSIZE** el socket es de tipo **SOCK_DGRAM**, y el datagrama es mayor que el límite máximo admitido por la implementación de Windows Sockets.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido a tiempo de espera u otro error.  
  
- **WSAECONNRESET** se restableció el circuito virtual en el lado remoto.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAEDESTADDRREQ** se necesita una dirección de destino.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
### <a name="remarks"></a>Comentarios  
 `SendTo` se usa en sockets de datagramas o la secuencia y se usa para escribir los datos salientes en un socket. Para los sockets de datagramas, se debe tener cuidado de no debe superar el tamaño máximo de paquetes IP de las subredes subyacentes, que viene dada por la **iMaxUdpDg** elemento en el [WSADATA](../../mfc/reference/wsadata-structure.md) estructura rellenado por [ AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos son demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error **WSAEMSGSIZE** se devuelve, y se transmite ningún dato.  
  
 Tenga en cuenta que la finalización correcta de una `SendTo` no indica que los datos se ha entregado correctamente.  
  
 `SendTo` solo se usa en un **SOCK_DGRAM** socket para enviar un datagrama a un socket específico identificado por la *lpSockAddr* parámetro.  
  
 Para enviar una difusión (en un **SOCK_DGRAM** solo), la dirección en la *lpSockAddr* parámetro debe crearse con la dirección IP especial **INADDR_BROADCAST** (definido en el encabezado de Windows Sockets archivo WINSOCK. (H) junto con el número de puerto deseado. O bien, si la *lpszHostAddress* parámetro es **NULL**, el socket está configurado para la difusión. No es recomendable generalmente para un datagrama difusión supere el tamaño en el que puede producir una fragmentación, lo cual implica que la parte de datos del datagrama (excluyendo encabezados) no debe superar los 512 bytes.  
  
 Para controlar las direcciones IPv6, use [CAsyncSocket::SendToEx](#sendtoex).  
  
##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx  
 Llame a esta función miembro para enviar datos a un destino concreto (identificadores de direcciones IPv6).  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpBuf*  
 Un búfer que contiene los datos que se transmitan.  
  
 *nBufLen*  
 La longitud de los datos de *lpBuf* en bytes.  
  
 *nHostPort*  
 El puerto identifica la aplicación de socket.  
  
 *lpszHostAddress*  
 La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número separado por puntos, como "128.56.22.8".  
  
 *nFlags*  
 Especifica la manera en que se realiza la llamada. La semántica de esta función está determinada por las opciones de socket y *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:  
  
- **MSG_DONTROUTE** especifica que los datos no deben estar sujeta a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.  
  
- **MSG_OOB** enviar datos fuera de banda ( **SOCK_STREAM** solo).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `SendToEx` devuelve el número total de caracteres que se envían. (Tenga en cuenta que puede ser menor que el número indicado por *nBufLen*.) En caso contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEACCES** la dirección solicitada es una dirección de difusión, pero no se estableció el marcador adecuado.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEFAULT** el *lpBuf* o *lpSockAddr* parámetros no forman parte del espacio de direcciones del usuario, o la *lpSockAddr* argumento (menor que el tamaño es demasiado pequeño de un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINVAL** el nombre de host no es válido.  
  
- **WSAENETRESET** se debe restablecer la conexión porque la implementación de Windows Sockets quitó.  
  
- **WSAENOBUFS** implementación de los Sockets de Windows notifica un interbloqueo de búfer.  
  
- **WSAENOTCONN** el socket no está conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `SendToEx` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 1 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como sin bloqueo y bloqueará la operación solicitada.  
  
- **WSAEMSGSIZE** el socket es de tipo **SOCK_DGRAM**, y el datagrama es mayor que el límite máximo admitido por la implementación de Windows Sockets.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido a tiempo de espera u otro error.  
  
- **WSAECONNRESET** se restableció el circuito virtual en el lado remoto.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAEDESTADDRREQ** se necesita una dirección de destino.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
### <a name="remarks"></a>Comentarios  
 Este método es el mismo que [:: SendTo](#sendto) salvo que es capaz de abrir IPv6 protocolos anteriores, así como las direcciones.  
  
 `SendToEx` se usa en sockets de datagramas o la secuencia y se usa para escribir los datos salientes en un socket. Para los sockets de datagramas, se debe tener cuidado de no debe superar el tamaño máximo de paquetes IP de las subredes subyacentes, que viene dada por la **iMaxUdpDg** elemento en el [WSADATA](../../mfc/reference/wsadata-structure.md) estructura rellenado por [ AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos son demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error **WSAEMSGSIZE** se devuelve, y se transmite ningún dato.  
  
 Tenga en cuenta que la finalización correcta de una `SendToEx` no indica que los datos se ha entregado correctamente.  
  
 `SendToEx` solo se usa en un **SOCK_DGRAM** socket para enviar un datagrama a un socket específico identificado por la *lpSockAddr* parámetro.  
  
 Para enviar una difusión (en un **SOCK_DGRAM** solo), la dirección en la *lpSockAddr* parámetro debe crearse con la dirección IP especial **INADDR_BROADCAST** (definido en el encabezado de Windows Sockets archivo WINSOCK. (H) junto con el número de puerto deseado. O bien, si la *lpszHostAddress* parámetro es **NULL**, el socket está configurado para la difusión. No es recomendable generalmente para un datagrama difusión supere el tamaño en el que puede producir una fragmentación, lo cual implica que la parte de datos del datagrama (excluyendo encabezados) no debe superar los 512 bytes.  
  
##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt  
 Llame a esta función miembro para establecer una opción de socket.  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parámetros  
 *nOptionName*  
 La opción de socket para la que el valor va a establecerse.  
  
 *lpOptionValue*  
 Un puntero al búfer en el que se proporciona el valor de la opción solicitada.  
  
 *nOptionLen*  
 El tamaño de la *lpOptionValue* búfer en bytes.  
  
 *nLevel*  
 El nivel en el que se define la opción; los niveles admitidos solo son **SOL_SOCKET** y **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEFAULT** *lpOptionValue* no es una parte válida del espacio de direcciones del proceso.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAEINVAL** *nLevel* no es válido, o la información de *lpOptionValue* no es válido.  
  
- **WSAENETRESET** conexión ha agotado cuando **SO_KEEPALIVE** se establece.  
  
- **WSAENOPROTOOPT** la opción es desconocido o no es compatible. En concreto, **SO_BROADCAST** no se admite en sockets de tipo **SOCK_STREAM**, mientras que **SO_DONTLINGER**, **SO_KEEPALIVE**,  **SO_LINGER**, y **SO_OOBINLINE** no se admite en sockets de tipo **SOCK_DGRAM**.  
  
- **WSAENOTCONN** conexión ha sido restablecer cuando **SO_KEEPALIVE** se establece.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 `SetSockOpt` establece el valor actual de una opción de socket asociado con un socket de cualquier tipo, en cualquier estado. Aunque pueden existen opciones en varios niveles de protocolo, esta especificación solo define opciones que existen en el nivel superior "socket". Opciones afectan a las operaciones de socket, por ejemplo, si los datos inmediatos se reciben en el flujo de datos normal, si se pueden enviar en el socket de mensajes de difusión y así sucesivamente.  
  
 Hay dos tipos de opciones de socket: opciones booleanas que habilitar o deshabilitación una característica o el comportamiento y las opciones que requieren una estructura o un valor entero. Para habilitar una opción de booleana, *lpOptionValue* apunta a un entero distinto de cero. Para deshabilitar la opción *lpOptionValue* apunta a un entero igual a cero. *nOptionLen* debe ser igual a **sizeof(BOOL)** para opciones booleanas. Para ver otras opciones, *lpOptionValue* apunta al entero o estructura que contiene el valor deseado para la opción y *nOptionLen* es la longitud de la entero o la estructura.  
  
 **SO_LINGER** controles de la acción realizada cuando no enviado los datos se ponen en cola en un socket y `Close` función se invoca para cerrar el socket.  
  
 De forma predeterminada, no se puede enlazar un socket (vea [enlazar](#bind)) a una dirección local que ya está en uso. En ocasiones, sin embargo, puede ser deseable "volver" una dirección de esta manera. Puesto que todas las conexiones se identifican exclusivamente mediante la combinación de direcciones locales y remotas, no hay ningún problema de que dos sockets enlazados a la misma dirección local, como las direcciones remotas son diferentes.  
  
 Para informar a la implementación de Windows Sockets que un `Bind` llamada en un socket no debería admitirse porque la dirección deseada ya está en uso por otro socket, la aplicación debe establecer el **SO_REUSEADDR** opción de socket para el socket antes de emitir la `Bind` llamar. Tenga en cuenta que la opción se interpreta solo en el momento de la `Bind` llamar: por lo tanto, es necesario (pero es inofensiva) para establecer la opción en un socket que no esté enlazado a una dirección existente, y establecer o restablecer la opción después de la `Bind` llamada tiene ningún efecto en este u otro socket.  
  
 Una aplicación puede solicitar que la implementación de Windows Sockets habilitar el uso de paquetes "keep-alive" en las conexiones de protocolo de Control de transmisión (TCP) activando el **SO_KEEPALIVE** opción de socket. Una implementación de Windows Sockets no necesita admitir el uso de comandos keepalive: si lo hace, la semántica precisa son específicas de la implementación, pero debe ajustarse a la sección 4.2.3.6 de RFC 1122: "requisitos para Hosts de Internet: niveles de comunicación." Si una conexión se interrumpe el código de error como resultado de "abiertas" **WSAENETRESET** se devuelve para las llamadas en curso en el socket, y se producirá un error de las subsiguientes llamadas con **WSAENOTCONN**.  
  
 El **TCP_NODELAY** opción deshabilita el algoritmo de Nagle. Se utiliza el algoritmo de Nagle para reducir la cantidad de pequeños paquetes enviados por un host mediante el almacenamiento en búfer de datos de envío no reconocidos hasta que puede enviarse un paquete de tamaño completo. Sin embargo, para algunas aplicaciones de este algoritmo puede disminuir el rendimiento, y **TCP_NODELAY** puede utilizarse para desactivarlo. Escritores de aplicaciones no deben establecer **TCP_NODELAY** a menos que el efecto de hacerlo es deseado y también se entiende bien desde configuración **TCP_NODELAY** puede tener un efecto negativo importante en el rendimiento de red . **Tcp_nodelay** es el único admite la opción de socket que utiliza nivel **IPPROTO_TCP**; todas las demás opciones utilizan nivel **SOL_SOCKET**.  
  
 Algunas implementaciones de fuente de alimentación de Windows Sockets información de depuración de salida si el **SO_DEBUG** opción está establecida por una aplicación.  
  
 Se admiten las siguientes opciones para `SetSockOpt`. El tipo identifica el tipo de datos dirigidos por *lpOptionValue*.  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|Permitir la transmisión de mensajes de difusión en el socket.|  
|**SO_DEBUG**|**BOOL**|Registra información de depuración.|  
|**SO_DONTLINGER**|**BOOL**|No bloqueen **cerrar** esperando sin enviar datos que se enviarán. Esta opción es equivalente a establecer **SO_LINGER** con **l_onoff** establecido en cero.|  
|**SO_DONTROUTE**|**BOOL**|No enrutar: enviar directamente a la interfaz.|  
|**SO_KEEPALIVE**|**BOOL**|Enviar keepalive.|  
|**SO_LINGER**|**struct PERMANENCIA**|Demora **cerrar** si no enviado los datos están presentes.|  
|**SO_OOBINLINE**|**BOOL**|Recibir datos de fuera de banda en el flujo de datos normal.|  
|**SO_RCVBUF**|**int**|Especificar tamaño de búfer para recibe.|  
|**SO_REUSEADDR**|**BOOL**|Permitir que el socket esté enlazado a una dirección que ya está en uso. (Consulte [enlazar](#bind).)|  
|**SO_SNDBUF**|**int**|Especifique el tamaño de búfer para los envíos.|  
|**TCP_NODELAY**|**BOOL**|Deshabilita el algoritmo de Nagle para la fusión de envíos.|  
  
 Opciones de Berkeley Software Distribution (BSD) no se admite para `SetSockOpt` son:  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Socket está escuchando|  
|**SO_ERROR**|**int**|Obtiene el estado de error y borra.|  
|**SO_RCVLOWAT**|**int**|Recibir marca de agua suave.|  
|**SO_RCVTIMEO**|**int**|Tiempo de espera de recepción|  
|**SO_SNDLOWAT**|**int**|Enviar la marca de agua suave.|  
|**SO_SNDTIMEO**|**int**|Tiempo de espera de envío.|  
|**SO_TYPE**|**int**|Tipo del socket.|  
|**IP_OPTIONS**||Establezca el campo de opciones en el encabezado IP.|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 Llamada a esta función miembro para deshabilitar envía, recibe, o ambos en el socket.  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>Parámetros  
 *nHow*  
 Una marca que describe qué tipos de operación ya no se permitirá, mediante los valores enumerados siguientes:  
  
- **recibe = 0**  
  
- **envía = 1**  
  
- **tanto = 2**  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** una correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no se pudo.  
  
- **WSAEINVAL** *nHow* no es válido.  
  
- **WSAEINPROGRESS** una operación de Windows Sockets bloqueo está en curso.  
  
- **WSAENOTCONN** el socket no está conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 `ShutDown` se utiliza en todos los tipos de sockets para deshabilitar la recepción, transmisión o ambos. Si *nHow* es 0, que recibe subsiguientes en el socket no se permitirá. Esto no tiene ningún efecto en las capas de protocolo inferiores.  
  
 Para el protocolo de Control de transmisión (TCP), no se cambia la ventana TCP y los datos entrantes será aceptado (pero no confirmado) hasta que se agote la ventana. Para el protocolo de datagramas de usuario (UDP), los datagramas entrantes se aceptan y en cola. En ningún caso se generará un paquete de error ICMP. Si *nHow* es 1, no se permiten los envíos posteriores. Para los sockets TCP, se enviará un FIN. Establecer *nHow* a 2 deshabilita ambos envía y recibe como se describió anteriormente.  
  
 Tenga en cuenta que `ShutDown` no cerrar el socket y los recursos adjuntados al socket no se liberarán hasta que `Close` se llama. Una aplicación no debe confiar en que se va a reutilizar un socket después de que se ha apagado. En concreto, una implementación de Windows Sockets no es necesario para admitir el uso de `Connect` en un socket de este tipo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 Asigna un identificador de socket.  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>Parámetros  
 *nSocketType*  
 Especifica `SOCK_STREAM` o `SOCK_DGRAM`.  
  
 *lEvent*  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- `FD_READ`: Desea recibir una notificación de preparación para la lectura.  
  
- `FD_WRITE`: Desea recibir una notificación de preparación para escribir en él.  
  
- `FD_OOB`: Desea recibir una notificación de la llegada de datos fuera de banda.  
  
- `FD_ACCEPT`: Desea recibir una notificación de las conexiones entrantes.  
  
- `FD_CONNECT`: Desea recibir una notificación de conexión completada.  
  
- `FD_CLOSE`: Desea recibir una notificación de cierre del socket.  
  
 *nProtocolType*  
 Protocolo que se usará con el socket que es específico de la familia de direcciones indicado.  
  
 *nAddressFormat*  
 Especificación para la familia de direcciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la operación se realiza correctamente; de lo contrario, devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método asigna un identificador de socket. No llame [CAsyncSocket::Bind](#bind) para enlazar el socket a una dirección especificada, por lo que necesita llamar a `Bind` más adelante para enlazar el socket a una dirección especificada. Puede usar [CAsyncSocket::SetSockOpt](#setsockopt) para establecer la opción de socket antes de que está enlazado.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSocket (clase)](../../mfc/reference/csocket-class.md)   
 [CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
