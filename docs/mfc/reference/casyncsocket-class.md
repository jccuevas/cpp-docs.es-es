---
title: CAsyncSocket (clase)
ms.date: 09/03/2019
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
ms.openlocfilehash: 4e14052d400268a8852298113ba9b51fda713dc8
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273791"
---
# <a name="casyncsocket-class"></a>CAsyncSocket (clase)

Representa un socket de Windows, un extremo de comunicación de red.

## <a name="syntax"></a>Sintaxis

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Construye un objeto `CAsyncSocket`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncSocket::Accept](#accept)|Acepta una conexión en el socket.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Solicita la notificación de eventos para el socket.|
|[CAsyncSocket::Attach](#attach)|Asocia un identificador de socket a un `CAsyncSocket` objeto.|
|[CAsyncSocket::Bind](#bind)|Asocia una dirección local al socket.|
|[CAsyncSocket::Close](#close)|Cierra el socket.|
|[CAsyncSocket::Connect](#connect)|Establece una conexión con un socket del mismo nivel.|
|[CAsyncSocket::Create](#create)|Crea un socket.|
|[CAsyncSocket::Detach](#detach)|Desasocia un identificador de socket de `CAsyncSocket` un objeto.|
|[CAsyncSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CAsyncSocket` objeto, dado un identificador de socket.|
|[CAsyncSocket::GetLastError](#getlasterror)|Obtiene el estado de error de la última operación en la que se produjo un error.|
|[CAsyncSocket::GetPeerName](#getpeername)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket (controla las direcciones IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Obtiene el nombre local de un socket.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtiene el nombre local de un socket (controla las direcciones IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Recupera una opción de socket.|
|[CAsyncSocket::IOCtl](#ioctl)|Controla el modo del socket.|
|[CAsyncSocket::Listen](#listen)|Establece un socket para escuchar las solicitudes de conexión entrantes.|
|[CAsyncSocket::Receive](#receive)|Recibe datos del socket.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Recibe un datagrama y almacena la dirección de origen.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Recibe un datagrama y almacena la dirección de origen (controla las direcciones IPv6).|
|[CAsyncSocket::Send](#send)|Envía datos a un socket conectado.|
|[CAsyncSocket::SendTo](#sendto)|Envía datos a un destino específico.|
|[CAsyncSocket::SendToEx](#sendtoex)|Envía datos a un destino específico (controla las direcciones IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Establece una opción de socket.|
|[CAsyncSocket::ShutDown](#shutdown)|Deshabilita `Send`ollamaaenel Socket.`Receive`|
|[CASyncSocket::Socket](#socket)|Asigna un identificador de socket.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Notifica a un socket de escucha que puede aceptar solicitudes de conexión pendientes mediante `Accept`una llamada a.|
|[CAsyncSocket::OnClose](#onclose)|Notifica a un socket que el socket conectado a él se ha cerrado.|
|[CAsyncSocket::OnConnect](#onconnect)|Notifica a un socket de conexión que el intento de conexión se ha completado, ya sea correctamente o con error.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Notifica a un socket de recepción que hay datos fuera de banda que se van a leer en el socket, normalmente un mensaje urgente.|
|[CAsyncSocket::OnReceive](#onreceive)|Notifica a un socket de escucha que hay datos que se van a recuperar `Receive`llamando a.|
|[CAsyncSocket::OnSend](#onsend)|Notifica a un socket que puede enviar datos mediante una llamada `Send`a.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|Asigna un nuevo valor a un `CAsyncSocket` objeto.|
|[CAsyncSocket:: Operator (SOCKET)](#operator_socket)|Utilice este operador para recuperar el identificador de socket del `CAsyncSocket` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indica el identificador de socket asociado a `CAsyncSocket` este objeto.|

## <a name="remarks"></a>Comentarios

La `CAsyncSocket` clase encapsula la API de funciones de socket de Windows, que proporciona una abstracción orientada a objetos para los programadores que desean usar Windows Sockets junto con MFC.

Esta clase se basa en la suposición de que entiende las comunicaciones de red. Usted es responsable de controlar el bloqueo, las diferencias de orden de bytes y las conversiones entre cadenas Unicode y de juegos de caracteres multibyte (MBCS). Si desea una interfaz más cómoda que administre estos problemas, vea la clase [CSocket](../../mfc/reference/csocket-class.md).

Para usar un `CAsyncSocket` objeto, llame a su constructor y, a continuación, llame a la función [Create](#create) para crear el `SOCKET`identificador de socket subyacente (Type), excepto en los sockets aceptados. Para un socket de servidor, llame a la función miembro [Listen](#listen) y, para un socket de cliente, llame a la función miembro [Connect](#connect) . El socket de servidor debe llamar a la función [Accept](#accept) al recibir una solicitud de conexión. Use las funciones `CAsyncSocket` restantes para llevar a cabo las comunicaciones entre los sockets. Al finalizar, destruya el `CAsyncSocket` objeto si se creó en el montón; el destructor llama automáticamente a la función [Close](#close) . El tipo de datos socket se describe en el [artículo Windows Sockets: En](../../mfc/windows-sockets-background.md)segundo plano.

> [!NOTE]
>  Al utilizar sockets de MFC en subprocesos secundarios en una aplicación MFC vinculada estáticamente `AfxSocketInit` , debe llamar a en cada subproceso que use Sockets para inicializar las bibliotecas de Sockets. De forma predeterminada `AfxSocketInit` , solo se llama en el subproceso principal.

Para obtener más información, [vea Windows Sockets: Usar la clase](../../mfc/windows-sockets-using-class-casyncsocket.md) CAsyncSocket y los artículos relacionados, así como la [API de Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Requisitos

**Encabezado:** AfxSock. h

##  <a name="accept"></a>  CAsyncSocket::Accept

Llame a esta función miembro para aceptar una conexión en un socket.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parámetros

*rConnectedSocket*<br/>
Referencia que identifica un nuevo socket que está disponible para la conexión.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que recibe la dirección del socket que se conecta, como se conoce en la red. El formato exacto del argumento *lpSockAddr* viene determinado por la familia de direcciones establecida cuando se creó el socket. Si *lpSockAddr* y/o *lpSockAddrLen* son iguales a NULL, no se devuelve información sobre la dirección remota del socket aceptado.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección en *lpSockAddr* en bytes. *LpSockAddrLen* es un parámetro de resultado de valor: debe contener inicialmente la cantidad de espacio a la que apunta *lpSockAddr*. en la devolución, contendrá la longitud real (en bytes) de la dirección devuelta.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* es demasiado pequeño (menor que el tamaño de una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS una llamada de bloqueo de Windows Sockets está en curso.

- No `Listen` se invocó WSAEINVAL antes de aceptar.

- WSAEMFILE la cola está vacía cuando la entrada se acepta y no hay ningún descriptor disponible.

- WSAENOBUFS no hay espacio en búfer disponible.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEOPNOTSUPP el socket al que se hace referencia no es un tipo que admita el servicio orientado a la conexión.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y no hay ninguna conexión presente para aceptarlo.

### <a name="remarks"></a>Comentarios

Esta rutina extrae la primera conexión en la cola de conexiones pendientes, crea un nuevo socket con las mismas propiedades que este socket y lo adjunta a *rConnectedSocket*. Si no hay ninguna conexión pendiente en la cola, `Accept` devuelve cero y `GetLastError` devuelve un error. El socket aceptado ( *rConnectedSocket)* no se puede usar para aceptar más conexiones. El socket original permanece abierto y escuchando.

El argumento *lpSockAddr* es un parámetro de resultado que se rellena con la dirección del socket que se conecta, como se conoce en el nivel de comunicaciones. `Accept`se usa con tipos de socket basados en conexión como SOCK_STREAM.

##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect

Llame a esta función miembro para solicitar la notificación de eventos de un socket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parámetros

*lEvent*<br/>
Máscara de máscara que especifica una combinación de eventos de red en los que está interesado la aplicación.

- FD_READ desea recibir notificaciones de preparación para la lectura.

- FD_WRITE desea recibir una notificación cuando los datos estén disponibles para su lectura.

- FD_OOB desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT desea recibir una notificación de los resultados de la conexión.

- FD_CLOSE desea recibir una notificación cuando un punto de conexión ha sido cerrado por un elemento del mismo nivel.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEINVAL indica que uno de los parámetros especificados no era válido.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

### <a name="remarks"></a>Comentarios

Esta función se usa para especificar qué funciones de notificación de devolución de llamada de MFC se llamarán para el socket. `AsyncSelect`establece automáticamente este socket en modo de no bloqueo. Para obtener más información, vea el [artículo Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="attach"></a>  CAsyncSocket::Attach

Llame a esta función miembro para adjuntar el identificador `CAsyncSocket` *hSocket* a un objeto.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

*lEvent*<br/>
Máscara de máscara que especifica una combinación de eventos de red en los que está interesado la aplicación.

- FD_READ desea recibir notificaciones de preparación para la lectura.

- FD_WRITE desea recibir una notificación cuando los datos estén disponibles para su lectura.

- FD_OOB desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT desea recibir una notificación de los resultados de la conexión.

- FD_CLOSE desea recibir una notificación cuando un punto de conexión ha sido cerrado por un elemento del mismo nivel.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente.

### <a name="remarks"></a>Comentarios

El identificador de SOCKET se almacena en el miembro de datos [m_hSocket](#m_hsocket) del objeto.

##  <a name="bind"></a>  CAsyncSocket::Bind

Llame a esta función miembro para asociar una dirección local al socket.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszSocketAddress*<br/>
La dirección de red, un número de puntos como "128.56.22.8". Al pasar la cadena null para este parámetro, `CAsyncSocket` se indica que la instancia debe escuchar la actividad del cliente en todas las interfaces de red.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección que se va a asignar a este socket.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). En la lista siguiente se describen algunos de los errores que se pueden devolver. Para obtener una lista completa, consulte [códigos de error de Windows Sockets](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEADDRINUSE la dirección especificada ya está en uso. (Consulte la [opción de socket SO_REUSEADDR en la](#setsockopt)sección de la.)

- WSAEFAULT el argumento *nSockAddrLen* es demasiado pequeño (menor que el tamaño de una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS una llamada de bloqueo de Windows Sockets está en curso.

- WSAEAFNOSUPPORT la familia de direcciones especificada no es compatible con este puerto.

- WSAEINVAL el socket ya está enlazado a una dirección.

- WSAENOBUFS no hay suficientes búferes disponibles, demasiadas conexiones.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Esta rutina se usa en un datagrama no conectado o en un socket de flujo, `Connect` antes `Listen` de las llamadas posteriores o. Antes de que pueda aceptar solicitudes de conexión, un socket del servidor de escucha debe seleccionar un número de puerto y hacer que Windows Sockets `Bind`lo sepa llamando a. `Bind`establece la asociación local (número de puerto/dirección de host) del socket mediante la asignación de un nombre local a un socket sin nombre.

##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket

Construye un objeto socket en blanco.

```
CAsyncSocket();
```

### <a name="remarks"></a>Comentarios

Después de construir el objeto, debe llamar a su `Create` función miembro para crear la estructura de datos de socket y enlazar su dirección. (En el lado del servidor de una comunicación de Windows Sockets, cuando el socket de escucha crea un socket para `Accept` usarlo en la llamada, no `Create` se llama a para ese socket).

##  <a name="close"></a>  CAsyncSocket::Close

Cierra el socket.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Esta función libera el descriptor de socket para que se produzcan errores en otras referencias a él con el error WSAENOTSOCK. Si se trata de la última referencia al socket subyacente, la información de nomenclatura asociada y los datos en cola se descartan. El destructor del objeto de socket `Close` llama a usted.

Para `CAsyncSocket`, pero no para `CSocket`, la semántica de se `Close` ve afectada por las opciones de socket SO_LINGER y SO_DONTLINGER. Para obtener más información, vea función `GetSockOpt`miembro.

##  <a name="connect"></a>  CAsyncSocket::Connect

Llame a esta función miembro para establecer una conexión con una secuencia o un socket de datagramas no conectados.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parámetros

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo como "ftp.microsoft.com" o un número de puntos como "128.56.22.8".

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección del socket conectado.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Si esto indica un código de error de WSAEWOULDBLOCK y la aplicación utiliza las devoluciones de llamada reemplazables, la aplicación recibirá un `OnConnect` mensaje cuando se complete la operación de conexión. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEADDRINUSE la dirección especificada ya está en uso.

- WSAEINPROGRESS una llamada de bloqueo de Windows Sockets está en curso.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden usar con este socket.

- WSAECONNREFUSED se rechazó el intento de conexión.

- WSAEDESTADDRREQ se requiere una dirección de destino.

- WSAEFAULT el argumento *nSockAddrLen* es incorrecto.

- WSAEINVAL dirección de host no válida.

- WSAEISCONN el socket ya está conectado.

- WSAEMFILE no hay más descriptores de archivo disponibles.

- WSAENETUNREACH no se puede acceder a la red desde este host en este momento.

- WSAENOBUFS no hay espacio en búfer disponible. No se puede conectar el socket.

- WSAENOTSOCK el descriptor no es un socket.

- WSAETIMEDOUT intento de conexión ha agotado el tiempo de espera sin establecer una conexión.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la conexión no se puede completar inmediatamente.

### <a name="remarks"></a>Comentarios

Si el socket es independiente, el sistema asigna valores únicos a la asociación local y el socket se marca como enlazado. Tenga en cuenta que si el campo Dirección de la estructura de nombre es cero `Connect` , devolverá cero. Para obtener información de error extendida, `GetLastError` llame a la función miembro.

En el caso de sockets de secuencias (tipo SOCK_STREAM), se inicia una conexión activa al host externo. Cuando la llamada de socket se completa correctamente, el socket está listo para enviar o recibir datos.

Para un socket de datagrama (tipo SOCK_DGRAM), se establece un destino predeterminado, que se usará en las `Send` llamadas `Receive` y posteriores.

##  <a name="create"></a>  CAsyncSocket::Create

Llame a `Create` la función miembro después de construir un objeto socket para crear el socket de Windows y adjuntarlo.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
Un puerto conocido que se utilizará con el socket, o 0 si desea que Windows Sockets Seleccione un puerto.

*nSocketType*<br/>
SOCK_STREAM o SOCK_DGRAM.

*lEvent*<br/>
Máscara de máscara que especifica una combinación de eventos de red en los que está interesado la aplicación.

- FD_READ desea recibir notificaciones de preparación para la lectura.

- FD_WRITE desea recibir notificaciones de preparación para la escritura.

- FD_OOB desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT desea recibir una notificación de la conexión completada.

- FD_CLOSE desea recibir una notificación de cierre del socket.

*lpszSockAddress*<br/>
Un puntero a una cadena que contiene la dirección de red del socket conectado, un número de puntos como "128.56.22.8". Al pasar la cadena null para este parámetro, `CAsyncSocket` se indica que la instancia debe escuchar la actividad del cliente en todas las interfaces de red.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEAFNOSUPPORT no se admite la familia de direcciones especificada.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEMFILE no hay más descriptores de archivo disponibles.

- WSAENOBUFS no hay espacio en búfer disponible. No se puede crear el socket.

- WSAEPROTONOSUPPORT el puerto especificado no es compatible.

- WSAEPROTOTYPE el puerto especificado es un tipo incorrecto para este socket.

- WSAESOCKTNOSUPPORT el tipo de socket especificado no se admite en esta familia de direcciones.

### <a name="remarks"></a>Comentarios

`Create`llama a [socket](#socket) y, si se realiza correctamente, llama a [BIND](#bind) para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:

- SOCK_STREAM proporciona secuencias de bytes secuenciadas, confiables y de dúplex completo basadas en conexión. Usa el protocolo de control de transmisión (TCP) para la familia de direcciones de Internet.

- SOCK_DGRAM admite datagramas, que son paquetes no confiables sin conexión de una longitud máxima fija (normalmente pequeña). Usa el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet.

    > [!NOTE]
    >  La `Accept` función miembro toma una referencia a un nuevo objeto vacío `CSocket` como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Tenga en cuenta que si este objeto de socket sale del ámbito, la conexión se cierra. No llame a `Create` para este nuevo objeto de socket.

> [!IMPORTANT]
> `Create`**no** es seguro para subprocesos.  Si lo llama en un entorno de varios subprocesos donde podría ser invocado simultáneamente por subprocesos diferentes, asegúrese de proteger cada llamada con una exclusión mutua u otro bloqueo de sincronización.

Para obtener más información sobre los sockets de flujo y de datagramas, vea los artículos [Windows Sockets: Background](../../mfc/windows-sockets-background.md) y[Windows Sockets: Puertos y direcciones](../../mfc/windows-sockets-ports-and-socket-addresses.md) de socket y la [API de Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>  CAsyncSocket::Detach

Llame a esta función miembro para desasociar el identificador de socket del miembro de `CAsyncSocket` datos m_hSocket del objeto y establecer *m_hSocket* en NULL.

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle

Devuelve un puntero a un `CAsyncSocket` objeto.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CAsyncSocket` objeto o null si no hay ningún `CAsyncSocket` objeto asociado a *hSocket*.

### <a name="remarks"></a>Comentarios

Cuando se especifica un identificador de socket, `CAsyncSocket` si un objeto no está asociado al identificador, la función miembro devuelve NULL.

##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError

Llame a esta función miembro para obtener el estado de error de la última operación en la que se produjo un error.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto indica el código de error de la última rutina de la API de Windows Sockets realizada por este subproceso.

### <a name="remarks"></a>Comentarios

Cuando una función miembro determinada indica que se ha producido un error `GetLastError` , se debe llamar a para recuperar el código de error adecuado. Vea las descripciones de las funciones miembro individuales para obtener una lista de los códigos de error aplicables.

Para obtener más información sobre los códigos de error, consulte la [API de Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName

Llame a esta función miembro para obtener la dirección del socket del mismo nivel al que está conectado este socket.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parámetros

*rPeerAddress*<br/>
Referencia a un `CString` objeto que recibe una dirección IP de número de puntos.

*rPeerPort*<br/>
Referencia a un UINT que almacena un puerto.

*lpSockAddr*<br/>
Puntero a la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que recibe el nombre del socket del mismo nivel.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección en *lpSockAddr* en bytes. En la devolución, el argumento *lpSockAddrLen* contiene el tamaño real de *lpSockAddr* devuelto en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* no es suficientemente grande.

- WSAEINPROGRESS una llamada de bloqueo de Windows Sockets está en curso.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Para controlar las direcciones IPv6, use [CAsyncSocket:: GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx

Llame a esta función miembro para obtener la dirección del socket del mismo nivel al que está conectado este socket (controla las direcciones IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parámetros

*rPeerAddress*<br/>
Referencia a un `CString` objeto que recibe una dirección IP de número de puntos.

*rPeerPort*<br/>
Referencia a un UINT que almacena un puerto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* no es suficientemente grande.

- WSAEINPROGRESS una llamada de bloqueo de Windows Sockets está en curso.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Esta función es igual que [CAsyncSocket:: GetPeerName](#getpeername) , con la diferencia de que controla las direcciones IPv6 y los protocolos antiguos.

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

*rSocketAddress*<br/>
Referencia a un `CString` objeto que recibe una dirección IP de número de puntos.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que recibe la dirección del socket.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* no es suficientemente grande.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEINVAL el socket no se ha enlazado a una dirección `Bind`con.

### <a name="remarks"></a>Comentarios

Esta llamada es especialmente útil cuando se `Connect` ha realizado una llamada sin hacer un `Bind` primero; esta llamada proporciona el único medio por el que se puede determinar la asociación local establecida por el sistema.

Para controlar las direcciones IPv6, use [CAsyncSocket:: GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx

Llame a esta función miembro para obtener el nombre local de un socket (controla las direcciones IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parámetros

*rSocketAddress*<br/>
Referencia a un `CString` objeto que recibe una dirección IP de número de puntos.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* no es suficientemente grande.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEINVAL el socket no se ha enlazado a una dirección `Bind`con.

### <a name="remarks"></a>Comentarios

Esta llamada es igual que [CAsyncSocket:: getsockname](#getsockname) , salvo que controla las direcciones IPv6 y los protocolos antiguos.

Esta llamada es especialmente útil cuando se `Connect` ha realizado una llamada sin hacer un `Bind` primero; esta llamada proporciona el único medio por el que se puede determinar la asociación local establecida por el sistema.

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

*nOptionName*<br/>
Opción de socket para la que se va a recuperar el valor.

*lpOptionValue*<br/>
Puntero al búfer en el que se va a devolver el valor de la opción solicitada. El valor asociado a la opción seleccionada se devuelve en el búfer *lpOptionValue*. El entero al que apunta *lpOptionLen* debe contener originalmente el tamaño de este búfer en bytes; y, en la devolución, se establecerá en el tamaño del valor devuelto. En el caso de SO_LINGER, será el tamaño de `LINGER` una estructura; para todas las demás opciones, será el tamaño de un valor booleano o **int**, dependiendo de la opción. Consulte la lista de opciones y sus tamaños en la sección Comentarios.

*lpOptionLen*<br/>
Puntero al tamaño del búfer de *lpOptionValue* en bytes.

*nLevel*<br/>
Nivel en el que se define la opción; los únicos niveles admitidos son SOL_SOCKET y IPPROTO_TCP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Si una opción nunca se estableció con `SetSockOpt` `GetSockOpt` , devuelve el valor predeterminado de la opción. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpOptionLen* no era válido.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAENOPROTOOPT: la opción es desconocida o no es compatible. En concreto, SO_BROADCAST no se admite en sockets de tipo SOCK_STREAM, mientras que SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER y SO_OOBINLINE no se admiten en sockets de tipo SOCK_DGRAM.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

`GetSockOpt`Recupera el valor actual de una opción de socket asociada a un socket de cualquier tipo, en cualquier Estado, y almacena el resultado en *lpOptionValue*. Las opciones afectan a las operaciones de socket, como el enrutamiento de paquetes, la transferencia de datos fuera de banda, etc.

Se admiten las siguientes opciones `GetSockOpt`para. El tipo identifica el tipo de datos direccionados por *lpOptionValue*. La opción TCP_NODELAY usa el nivel IPPROTO_TCP; todas las demás opciones usan el nivel SOL_SOCKET.

|Valor|Type|Significado|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|El socket está escuchando.|
|SO_BROADCAST|BOOL|Socket está configurado para la transmisión de mensajes de difusión.|
|SO_DEBUG|BOOL|La depuración está habilitada.|
|SO_DONTLINGER|BOOL|Si es true, la opción SO_LINGER está deshabilitada.|
|SO_DONTROUTE|BOOL|El enrutamiento está deshabilitado.|
|SO_ERROR|**int**|Recupere el estado de error y desactívela.|
|SO_KEEPALIVE|BOOL|Se están enviando conexiones persistentes.|
|SO_LINGER|`struct LINGER`|Devuelve las opciones de permanencia actual.|
|SO_OOBINLINE|BOOL|Los datos fuera de banda se reciben en el flujo de datos normal.|
|SO_RCVBUF|int|Tamaño de búfer para las recepciones.|
|SO_REUSEADDR|BOOL|El socket se puede enlazar a una dirección que ya está en uso.|
|SO_SNDBUF|**int**|Tamaño de búfer para los envíos.|
|SO_TYPE|**int**|El tipo del socket (por ejemplo, SOCK_STREAM).|
|TCP_NODELAY|BOOL|Deshabilita el algoritmo de Nagle para la fusión de envíos.|

Las opciones de distribución de software Berkeley (BSD) `GetSockOpt` no compatibles con son:

|Value|Type|Significado|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Recibir una marca de límite inferior.|
|SO_RCVTIMEO|**int**|Tiempo de espera de recepción.|
|SO_SNDLOWAT|**int**|Enviar marca de límite inferior.|
|SO_SNDTIMEO|**int**|Tiempo de espera de envío.|
|IP_OPTIONS||Obtiene opciones en el encabezado IP.|
|TCP_MAXSEG|**int**|Obtiene el tamaño máximo del segmento TCP.|

Si `GetSockOpt` se llama a con una opción no compatible, se producirá un código de error de `GetLastError`WSAENOPROTOOPT devuelto desde.

##  <a name="ioctl"></a>  CAsyncSocket::IOCtl

Llame a esta función miembro para controlar el modo de un socket.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parámetros

*lCommand*<br/>
Comando que se va a realizar en el socket.

*lpArgument*<br/>
Un puntero a un parámetro para *lCommand*.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEINVAL *lCommand* no es un comando válido o *lpArgument* no es un parámetro aceptable para *lCommand*, o bien el comando no es aplicable al tipo de socket proporcionado.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Esta rutina se puede usar en cualquier socket en cualquier estado. Se usa para obtener o recuperar los parámetros operativos asociados al socket, independientemente del protocolo y el subsistema de comunicaciones. Se admiten los siguientes comandos:

- FIONBIO habilita o deshabilita el modo de no bloqueo en el socket. El parámetro *lpArgument* apunta a un `DWORD`, que es distinto de cero si se va a habilitar el modo de no bloqueo y cero si se va a deshabilitar. Si `AsyncSelect` se ha emitido en un socket, cualquier intento de usar `IOCtl` para volver a establecer el socket en modo de bloqueo producirá un error con WSAEINVAL. Para volver a establecer el socket en modo de bloqueo y evitar el error WSAEINVAL, una aplicación debe `AsyncSelect` deshabilitarse primero llamando `AsyncSelect` a con el parámetro *lEvent* igual a `IOCtl`0 y, a continuación, llamar a.

- FIONREAD determinan el número máximo de bytes que se pueden leer `Receive` con una llamada de este socket. El parámetro *lpArgument* apunta a un `DWORD` en el `IOCtl` que almacena el resultado. Si este socket es de tipo SOCK_STREAM, FIONREAD devuelve la cantidad total de datos que se pueden leer en un único `Receive`; esto suele ser el mismo que la cantidad total de datos en cola en el socket. Si este socket es de tipo SOCK_DGRAM, FIONREAD devuelve el tamaño del primer datagrama en cola en el socket.

- SIOCATMARK determine si se han leído todos los datos fuera de banda. Esto se aplica solo a un socket de tipo SOCK_STREAM que se ha configurado para la recepción en línea de cualquier dato fuera de banda (SO_OOBINLINE). Si no hay datos fuera de banda esperando ser leídos, la operación devuelve un valor distinto de cero. En caso contrario, devuelve 0 y el `Receive` siguiente `ReceiveFrom` o el que se realiza en el socket recuperará algunos o todos los datos que preceden a la "marca"; la aplicación debe usar la operación SIOCATMARK para determinar si hay algún dato restante. Si hay datos normales que preceden a los datos "urgentes" (fuera de banda), se recibirán en orden. (Tenga en cuenta `Receive` que `ReceiveFrom` o nunca se combinarán datos fuera de banda y normales en la misma llamada). El parámetro *lpArgument* apunta a un `DWORD` en el `IOCtl` que almacena el resultado.

Esta función es un subconjunto `ioctl()` de tal y como se usa en los sockets de Berkeley. En concreto, no hay ningún comando que sea equivalente a FIOASYNC, mientras que SIOCATMARK es el único comando de nivel de socket que se admite.

##  <a name="listen"></a>CAsyncSocket:: Listen

Llame a esta función miembro para escuchar las solicitudes de conexión entrantes.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parámetros

*nConnectionBacklog*<br/>
La longitud máxima a la que puede crecer la cola de conexiones pendientes. El intervalo válido es de 1 a 5.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEADDRINUSE se ha intentado realizar escuchas en una dirección en uso.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEINVAL el socket no se ha enlazado `Bind` con o ya está conectado.

- WSAEISCONN el socket ya está conectado.

- WSAEMFILE no hay más descriptores de archivo disponibles.

- WSAENOBUFS no hay espacio en búfer disponible.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEOPNOTSUPP el socket al que se hace referencia no es de un tipo `Listen` que admita la operación.

### <a name="remarks"></a>Comentarios

Para aceptar conexiones, el socket se crea primero con `Create`, un trabajo pendiente para las conexiones entrantes `Listen`se especifica con y, a continuación, `Accept`las conexiones se aceptan con. `Listen`solo se aplica a los sockets que admiten conexiones, es decir, las de tipo SOCK_STREAM. Este socket se pone en modo "pasivo", donde se reconocen las conexiones entrantes y se pone en cola la aceptación pendiente del proceso.

Esta función suele usarse en servidores (o en cualquier aplicación que desee aceptar conexiones) que podrían tener más de una solicitud de conexión a la vez: Si una solicitud de conexión llega con la cola completa, el cliente recibirá un error con una indicación de WSAECONNREFUSED.

`Listen`intenta continuar funcionando racionalmente cuando no hay puertos disponibles (descriptores). Aceptará conexiones hasta que se vacíe la cola. Si los puertos están disponibles, una llamada posterior `Listen` a `Accept` o rellenará la cola al "trabajo pendiente" actual o más reciente, si es posible, y reanudará la escucha de las conexiones entrantes.

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

Contiene el identificador de socket para el socket encapsulado por `CAsyncSocket` este objeto.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>  CAsyncSocket::OnAccept

Lo llama el marco de trabajo para notificar a un socket de escucha que puede aceptar solicitudes de conexión pendientes mediante una llamada a la función miembro [Accept](#accept) .

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
Error más reciente en un socket. Los siguientes códigos de error se aplican a la `OnAccept` función miembro:

- **0** la función se ejecutó correctamente.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

### <a name="remarks"></a>Comentarios

Para obtener más información, [vea Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onclose"></a>  CAsyncSocket::OnClose

Lo llama el marco de trabajo para notificar a este socket que el socket conectado está cerrado por su proceso.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
Error más reciente en un socket. Los siguientes códigos de error se aplican a la `OnClose` función miembro:

- **0** la función se ejecutó correctamente.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAECONNRESET la conexión se restableció por el lado remoto.

- WSAECONNABORTED la conexión se anuló debido a un tiempo de espera o a otro error.

### <a name="remarks"></a>Comentarios

Para obtener más información, [vea Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onconnect"></a>  CAsyncSocket::OnConnect

Lo llama el marco de trabajo para notificar a este socket de conexión que se ha completado su intento de conexión, ya sea correctamente o con error.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
Error más reciente en un socket. Los siguientes códigos de error se aplican a la `OnConnect` función miembro:

- **0** la función se ejecutó correctamente.

- WSAEADDRINUSE la dirección especificada ya está en uso.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden usar con este socket.

- WSAECONNREFUSED el intento de conexión se rechazó forzosamente.

- WSAEDESTADDRREQ se requiere una dirección de destino.

- WSAEFAULT el argumento *lpSockAddrLen* es incorrecto.

- WSAEINVAL el socket ya está enlazado a una dirección.

- WSAEISCONN el socket ya está conectado.

- WSAEMFILE no hay más descriptores de archivo disponibles.

- WSAENETUNREACH no se puede acceder a la red desde este host en este momento.

- WSAENOBUFS no hay espacio en búfer disponible. No se puede conectar el socket.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor es un archivo, no un socket.

- WSAETIMEDOUT el intento de conexión agotó el tiempo de espera sin establecer una conexión.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  En [CSocket](../../mfc/reference/csocket-class.md), nunca `OnConnect` se llama a la función de notificación. En el caso de las conexiones `Connect`, simplemente llame a, que devolverá cuando se complete la conexión (ya sea correctamente o con errores). Cómo se controlan las notificaciones de conexión es un detalle de la implementación de MFC.

Para obtener más información, [vea Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData

Lo llama el marco de trabajo para notificar al socket de recepción que el socket de envío tiene datos fuera de banda para enviar.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
Error más reciente en un socket. Los siguientes códigos de error se aplican a la `OnOutOfBandData` función miembro:

- **0** la función se ejecutó correctamente.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

### <a name="remarks"></a>Comentarios

Los datos fuera de banda son un canal lógicamente independiente que está asociado a cada par de sockets conectados de tipo SOCK_STREAM. El canal se usa generalmente para enviar datos urgentes.

MFC admite datos fuera de banda, pero no se recomienda que los `CAsyncSocket` usuarios de la clase lo usen. La forma más sencilla consiste en crear un segundo socket para pasar estos datos. Para obtener más información sobre los datos fuera de banda, vea [Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onreceive"></a>  CAsyncSocket::OnReceive

Lo llama el marco de trabajo para notificar a este socket que hay datos en el búfer que se pueden recuperar `Receive` mediante una llamada a la función miembro.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
Error más reciente en un socket. Los siguientes códigos de error se aplican a la `OnReceive` función miembro:

- **0** la función se ejecutó correctamente.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

### <a name="remarks"></a>Comentarios

Para obtener más información, [vea Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>  CAsyncSocket::OnSend

Lo llama el marco de trabajo para notificar al socket que ahora puede enviar datos llamando `Send` a la función miembro.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
Error más reciente en un socket. Los siguientes códigos de error se aplican a la `OnSend` función miembro:

- **0** la función se ejecutó correctamente.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

### <a name="remarks"></a>Comentarios

Para obtener más información, [vea Windows Sockets: Notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>CAsyncSocket:: Operator =

Asigna un nuevo valor a un `CAsyncSocket` objeto.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Referencia a un objeto existente `CAsyncSocket` .

### <a name="remarks"></a>Comentarios

Llame a esta función para copiar un `CAsyncSocket` objeto existente en `CAsyncSocket` otro objeto.

##  <a name="operator_socket"></a>CAsyncSocket:: Operator (SOCKET)

Utilice este operador para recuperar el identificador de socket del `CAsyncSocket` objeto.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, el identificador del objeto de SOCKET; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

Puede utilizar el identificador para llamar a las API de Windows directamente.

##  <a name="receive"></a>  CAsyncSocket::Receive

Llame a esta función miembro para recibir datos de un socket.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Búfer para los datos entrantes.

*nBufLen*<br/>
Longitud de *lpBuf* en bytes.

*nFlags*<br/>
Especifica el modo en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el parámetro *nFlags* . Este último se construye mediante la combinación de cualquiera de los siguientes valores C++ con el operador **or** :

- MSG_PEEK PEEK en los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- MSG_OOB procesar los datos fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si no se produce ningún `Receive` error, devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAENOTCONN el socket no está conectado.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es del tipo SOCK_STREAM.

- WSAESHUTDOWN el socket se ha cerrado; no es posible llamar `Receive` a en un socket después `ShutDown` de que se haya invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la `Receive` operación se bloquearía.

- WSAEMSGSIZE el datagrama era demasiado grande para caber en el búfer especificado y se truncó.

- WSAEINVAL el socket no se ha enlazado `Bind`con.

- WSAECONNABORTED el circuito virtual se anuló debido a un tiempo de espera o a otro error.

- WSAECONNRESET el circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Comentarios

Esta función se usa para Sockets de datagramas o flujos conectados y se utiliza para leer los datos entrantes.

En el caso de los sockets de tipo SOCK_STREAM, se devuelve toda la información que esté disponible actualmente hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y los datos fuera de banda no se leen, solo se devolverán los datos fuera de banda. La aplicación puede usar la `IOCtlSIOCATMARK` opción o [OnOutOfBandData](#onoutofbanddata) para determinar si es necesario leer más datos fuera de banda.

En el caso de los sockets de datagramas, los datos se extraen del primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del datagrama, se pierden los datos sobrantes y `Receive` devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE. Si no hay datos entrantes disponibles en el socket, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. La función de devolución de llamada [alreceive](#onreceive) se puede usar para determinar cuándo llegan más datos.

Si el socket es de tipo SOCK_STREAM y el lado remoto ha cerrado la conexión correctamente, `Receive` se completará inmediatamente con 0 bytes recibidos. Si se ha restablecido la conexión, se `Receive` producirá un error WSAECONNRESET.

`Receive`solo se debe llamar una vez para cada vez que se llama a [CAsyncSocket:: alreceive](#onreceive) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket:: alreceive](#onreceive).

##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom

Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) o en *rSocketAddress*.

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

*lpBuf*<br/>
Búfer para los datos entrantes.

*nBufLen*<br/>
Longitud de *lpBuf* en bytes.

*rSocketAddress*<br/>
Referencia a un `CString` objeto que recibe una dirección IP de número de puntos.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección de origen al volver.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección de origen en *lpSockAddr* en bytes.

*nFlags*<br/>
Especifica el modo en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el parámetro *nFlags* . Este último se construye mediante la combinación de cualquiera de los siguientes valores C++ con el operador **or** :

- MSG_PEEK PEEK en los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- MSG_OOB procesar los datos fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si no se produce ningún `ReceiveFrom` error, devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar `GetLastError`llamando a. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* no era válido: el búfer *lpSockAddr* era demasiado pequeño para acomodar la dirección del mismo nivel.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEINVAL el socket no se ha enlazado `Bind`con.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es del tipo SOCK_STREAM.

- WSAESHUTDOWN el socket se ha cerrado; no es posible llamar `ReceiveFrom` a en un socket después `ShutDown` de que se haya invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la `ReceiveFrom` operación se bloquearía.

- WSAEMSGSIZE el datagrama era demasiado grande para caber en el búfer especificado y se truncó.

- WSAECONNABORTED el circuito virtual se anuló debido a un tiempo de espera o a otro error.

- WSAECONNRESET el circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Comentarios

Esta función se usa para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.

Para controlar las direcciones IPv6, use [CAsyncSocket:: ReceiveFromEx](#receivefromex).

En el caso de los sockets de tipo SOCK_STREAM, se devuelve toda la información que esté disponible actualmente hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y los datos fuera de banda no se leen, solo se devolverán los datos fuera de banda. La aplicación puede usar la `IOCtlSIOCATMARK` opción o `OnOutOfBandData` para determinar si hay más datos fuera de banda que quedan por leer. Los parámetros *lpSockAddr* y *lpSockAddrLen* se omiten para los sockets de SOCK_STREAM.

En el caso de los sockets de datagramas, los datos se extraen del primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del mensaje, se pierden los datos sobrantes y `ReceiveFrom` devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE.

Si *lpSockAddr* es distinto de cero y el socket es de tipo SOCK_DGRAM, la dirección de red del socket que envió los datos se copia en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) correspondiente. El valor al que apunta *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modifica en la devolución para indicar el tamaño real de la dirección almacenada en ella. Si no hay datos entrantes disponibles en el socket, `ReceiveFrom` la llamada espera a que lleguen los datos a menos que el socket no sea de bloqueo. En este caso, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. La `OnReceive` devolución de llamada se puede usar para determinar cuándo llegan más datos.

Si el socket es de tipo SOCK_STREAM y el lado remoto ha cerrado la conexión correctamente, `ReceiveFrom` se completará inmediatamente con 0 bytes recibidos.

##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx

Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) o en *rSocketAddress* (controla las direcciones IPv6).

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Búfer para los datos entrantes.

*nBufLen*<br/>
Longitud de *lpBuf* en bytes.

*rSocketAddress*<br/>
Referencia a un `CString` objeto que recibe una dirección IP de número de puntos.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

*nFlags*<br/>
Especifica el modo en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el parámetro *nFlags* . Este último se construye mediante la combinación de cualquiera de los siguientes valores C++ con el operador **or** :

- MSG_PEEK PEEK en los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- MSG_OOB procesar los datos fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si no se produce ningún `ReceiveFromEx` error, devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar `GetLastError`llamando a. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT el argumento *lpSockAddrLen* no era válido: el búfer *lpSockAddr* era demasiado pequeño para acomodar la dirección del mismo nivel.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEINVAL el socket no se ha enlazado `Bind`con.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es del tipo SOCK_STREAM.

- WSAESHUTDOWN el socket se ha cerrado; no es posible llamar `ReceiveFromEx` a en un socket después `ShutDown` de que se haya invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la `ReceiveFromEx` operación se bloquearía.

- WSAEMSGSIZE el datagrama era demasiado grande para caber en el búfer especificado y se truncó.

- WSAECONNABORTED el circuito virtual se anuló debido a un tiempo de espera o a otro error.

- WSAECONNRESET el circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Comentarios

Esta función se usa para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.

Esta función es igual que [CAsyncSocket:: ReceiveFrom](#receivefrom) , con la diferencia de que controla las direcciones IPv6 y los protocolos antiguos.

En el caso de los sockets de tipo SOCK_STREAM, se devuelve toda la información que esté disponible actualmente hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y los datos fuera de banda no se leen, solo se devolverán los datos fuera de banda. La aplicación puede usar la `IOCtlSIOCATMARK` opción o `OnOutOfBandData` para determinar si hay más datos fuera de banda que quedan por leer. Los parámetros *lpSockAddr* y *lpSockAddrLen* se omiten para los sockets de SOCK_STREAM.

En el caso de los sockets de datagramas, los datos se extraen del primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del mensaje, se pierden los datos sobrantes y `ReceiveFromEx` devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE.

Si *lpSockAddr* es distinto de cero y el socket es de tipo SOCK_DGRAM, la dirección de red del socket que envió los datos se copia en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) correspondiente. El valor al que apunta *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modifica en la devolución para indicar el tamaño real de la dirección almacenada en ella. Si no hay datos entrantes disponibles en el socket, `ReceiveFromEx` la llamada espera a que lleguen los datos a menos que el socket no sea de bloqueo. En este caso, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. La `OnReceive` devolución de llamada se puede usar para determinar cuándo llegan más datos.

Si el socket es de tipo SOCK_STREAM y el lado remoto ha cerrado la conexión correctamente, `ReceiveFromEx` se completará inmediatamente con 0 bytes recibidos.

##  <a name="send"></a>  CAsyncSocket::Send

Llame a esta función miembro para enviar datos en un socket conectado.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Búfer que contiene los datos que se van a transmitir.

*nBufLen*<br/>
La longitud de los datos en *lpBuf* en bytes.

*nFlags*<br/>
Especifica el modo en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el parámetro *nFlags* . Este último se construye mediante la combinación de cualquiera de los siguientes valores C++ con el operador **or** :

- MSG_DONTROUTE especifica que los datos no deben estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB enviar datos fuera de banda (solo SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Si no se produce ningún `Send` error, devuelve el número total de caracteres enviados. (Tenga en cuenta que puede ser menor que el número indicado por *nBufLen*). De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEACCES la dirección solicitada es una dirección de difusión, pero no se estableció la marca adecuada.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEFAULT el argumento *lpBuf* no está en una parte válida del espacio de direcciones del usuario.

- WSAENETRESET la conexión debe restablecerse porque la implementación de Windows Sockets la eliminó.

- WSAENOBUFS la implementación de Windows Sockets informa de un interbloqueo de búfer.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es del tipo SOCK_STREAM.

- WSAESHUTDOWN el socket se ha cerrado; no es posible llamar `Send` a en un socket después `ShutDown` de que se haya invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la operación solicitada se bloquearía.

- WSAEMSGSIZE el socket es de tipo SOCK_DGRAM y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.

- WSAEINVAL el socket no se ha enlazado `Bind`con.

- WSAECONNABORTED el circuito virtual se anuló debido a un tiempo de espera o a otro error.

- WSAECONNRESET el circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Comentarios

`Send`se utiliza para escribir los datos de salida en el flujo conectado o sockets de datagramas. En el caso de los sockets de datagrama, se debe tener cuidado de no superar el tamaño máximo de paquete IP de las subredes subyacentes, proporcionado por el `iMaxUdpDg` elemento de la estructura [wsadata (](/windows/win32/api/winsock2/ns-winsock2-wsadata) devuelta por. `AfxSocketInit` Si los datos son demasiado largos para pasar de forma atómica a través del protocolo subyacente, el WSAEMSGSIZE de error `GetLastError`se devuelve a través de y no se transmite ningún dato.

Tenga en cuenta que para un socket de datagrama la finalización correcta de un `Send` no indica que los datos se han entregado correctamente.

En `CAsyncSocket` objetos de tipo SOCK_STREAM, el número de bytes escritos puede estar entre 1 y la longitud solicitada, en función de la disponibilidad del búfer en los hosts locales y externos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket:: alsend](#onsend).

##  <a name="sendto"></a>  CAsyncSocket::SendTo

Llame a esta función miembro para enviar datos a un destino específico.

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

*lpBuf*<br/>
Búfer que contiene los datos que se van a transmitir.

*nBufLen*<br/>
La longitud de los datos en *lpBuf* en bytes.

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo como "ftp.microsoft.com" o un número de puntos como "128.56.22.8".

*nFlags*<br/>
Especifica el modo en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el parámetro *nFlags* . Este último se construye mediante la combinación de cualquiera de los siguientes valores C++ con el operador **or** :

- MSG_DONTROUTE especifica que los datos no deben estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB enviar datos fuera de banda (solo SOCK_STREAM).

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección del socket de destino.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Si no se produce ningún `SendTo` error, devuelve el número total de caracteres enviados. (Tenga en cuenta que puede ser menor que el número indicado por *nBufLen*). De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEACCES la dirección solicitada es una dirección de difusión, pero no se estableció la marca adecuada.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEFAULT los parámetros *lpBuf* o *lpSockAddr* no forman parte del espacio de direcciones del usuario, o el argumento *lpSockAddr* es demasiado pequeño (menor que el tamaño de una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINVAL el nombre de host no es válido.

- WSAENETRESET la conexión debe restablecerse porque la implementación de Windows Sockets la eliminó.

- WSAENOBUFS la implementación de Windows Sockets informa de un interbloqueo de búfer.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es del tipo SOCK_STREAM.

- WSAESHUTDOWN el socket se ha cerrado; no es posible llamar `SendTo` a en un socket después `ShutDown` de que se haya invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la operación solicitada se bloquearía.

- WSAEMSGSIZE el socket es de tipo SOCK_DGRAM y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.

- WSAECONNABORTED el circuito virtual se anuló debido a un tiempo de espera o a otro error.

- WSAECONNRESET el circuito virtual fue restablecido por el lado remoto.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden usar con este socket.

- WSAEDESTADDRREQ se requiere una dirección de destino.

- WSAENETUNREACH no se puede acceder a la red desde este host en este momento.

### <a name="remarks"></a>Comentarios

`SendTo`se utiliza en sockets de datagrama o de secuencia y se utiliza para escribir datos salientes en un socket. En el caso de los sockets de datagrama, se debe tener cuidado de no superar el tamaño máximo de los paquetes IP de las subredes `iMaxUdpDg` subyacentes, proporcionado por el elemento de la estructura [wsadata (](/windows/win32/api/winsock2/ns-winsock2-wsadata) rellenado por [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos son demasiado largos para pasar de forma atómica a través del protocolo subyacente, se devuelve el error WSAEMSGSIZE y no se transmite ningún dato.

Tenga en cuenta que la finalización `SendTo` correcta de un no indica que los datos se han entregado correctamente.

`SendTo`solo se usa en un socket SOCK_DGRAM para enviar un datagrama a un socket específico identificado por el parámetro *lpSockAddr* .

Para enviar una difusión (solo en un SOCK_DGRAM), la dirección del parámetro *lpSockAddr* debe construirse con la dirección IP especial INADDR_BROADCAST (definida en el archivo de encabezado Winsock de Windows Sockets). H) junto con el número de puerto previsto. O bien, si el parámetro *lpszHostAddress* es null, el socket se configura para la difusión. Por lo general, no es aconsejable que un datagrama de difusión supere el tamaño en el que puede producirse la fragmentación, lo que implica que la parte de datos del datagrama (excluidos los encabezados) no debe superar los 512 bytes.

Para controlar las direcciones IPv6, use [CAsyncSocket:: SendToEx](#sendtoex).

##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx

Llame a esta función miembro para enviar datos a un destino específico (controla las direcciones IPv6).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Búfer que contiene los datos que se van a transmitir.

*nBufLen*<br/>
La longitud de los datos en *lpBuf* en bytes.

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo como "ftp.microsoft.com" o un número de puntos como "128.56.22.8".

*nFlags*<br/>
Especifica el modo en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el parámetro *nFlags* . Este último se construye mediante la combinación de cualquiera de los siguientes valores C++ con el operador **or** :

- MSG_DONTROUTE especifica que los datos no deben estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB enviar datos fuera de banda (solo SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Si no se produce ningún `SendToEx` error, devuelve el número total de caracteres enviados. (Tenga en cuenta que puede ser menor que el número indicado por *nBufLen*). De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEACCES la dirección solicitada es una dirección de difusión, pero no se estableció la marca adecuada.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEFAULT los parámetros *lpBuf* o *lpSockAddr* no forman parte del espacio de direcciones del usuario, o el argumento *lpSockAddr* es demasiado pequeño (menor que el tamaño de una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINVAL el nombre de host no es válido.

- WSAENETRESET la conexión debe restablecerse porque la implementación de Windows Sockets la eliminó.

- WSAENOBUFS la implementación de Windows Sockets informa de un interbloqueo de búfer.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es del tipo SOCK_STREAM.

- WSAESHUTDOWN el socket se ha cerrado; no es posible llamar `SendToEx` a en un socket después `ShutDown` de que se haya invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK el socket está marcado como no bloqueado y la operación solicitada se bloquearía.

- WSAEMSGSIZE el socket es de tipo SOCK_DGRAM y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.

- WSAECONNABORTED el circuito virtual se anuló debido a un tiempo de espera o a otro error.

- WSAECONNRESET el circuito virtual fue restablecido por el lado remoto.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden usar con este socket.

- WSAEDESTADDRREQ se requiere una dirección de destino.

- WSAENETUNREACH no se puede acceder a la red desde este host en este momento.

### <a name="remarks"></a>Comentarios

Este método es el mismo que [CAsyncSocket:: SendTo](#sendto) , con la diferencia de que controla las direcciones IPv6 y los protocolos antiguos.

`SendToEx`se utiliza en sockets de datagrama o de secuencia y se utiliza para escribir datos salientes en un socket. En el caso de los sockets de datagrama, se debe tener cuidado de no superar el tamaño máximo de los paquetes IP de las subredes `iMaxUdpDg` subyacentes, proporcionado por el elemento de la estructura [wsadata (](/windows/win32/api/winsock2/ns-winsock2-wsadata) rellenado por [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos son demasiado largos para pasar de forma atómica a través del protocolo subyacente, se devuelve el error WSAEMSGSIZE y no se transmite ningún dato.

Tenga en cuenta que la finalización `SendToEx` correcta de un no indica que los datos se han entregado correctamente.

`SendToEx`solo se usa en un socket SOCK_DGRAM para enviar un datagrama a un socket específico identificado por el parámetro *lpSockAddr* .

Para enviar una difusión (solo en un SOCK_DGRAM), la dirección del parámetro *lpSockAddr* debe construirse con la dirección IP especial INADDR_BROADCAST (definida en el archivo de encabezado Winsock de Windows Sockets). H) junto con el número de puerto previsto. O bien, si el parámetro *lpszHostAddress* es null, el socket se configura para la difusión. Por lo general, no es aconsejable que un datagrama de difusión supere el tamaño en el que puede producirse la fragmentación, lo que implica que la parte de datos del datagrama (excluidos los encabezados) no debe superar los 512 bytes.

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

*nOptionName*<br/>
Opción de socket para la que se va a establecer el valor.

*lpOptionValue*<br/>
Puntero al búfer en el que se proporciona el valor de la opción solicitada.

*nOptionLen*<br/>
Tamaño del búfer de *lpOptionValue* en bytes.

*nLevel*<br/>
Nivel en el que se define la opción; los únicos niveles admitidos son SOL_SOCKET y IPPROTO_TCP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEFAULT *lpOptionValue* no es una parte válida del espacio de direcciones de proceso.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAEINVAL *nLevel* no es válido o la información de *lpOptionValue* no es válida.

- Se agotó el tiempo de espera de la conexión de WSAENETRESET al establecer SO_KEEPALIVE.

- WSAENOPROTOOPT: la opción es desconocida o no es compatible. En concreto, SO_BROADCAST no se admite en sockets de tipo SOCK_STREAM, mientras que SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER y SO_OOBINLINE no se admiten en sockets de tipo SOCK_DGRAM.

- Se ha restablecido la conexión de WSAENOTCONN cuando se establece SO_KEEPALIVE.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

`SetSockOpt`establece el valor actual de una opción de socket asociada a un socket de cualquier tipo, en cualquier estado. Aunque pueden existir opciones en varios niveles de protocolo, esta especificación solo define las opciones que existen en el nivel "socket" superior. Las opciones afectan a las operaciones de socket, como si se reciben datos inmediatos en el flujo de datos normal, si se pueden enviar mensajes de difusión en el socket, etc.

Hay dos tipos de opciones de socket: Opciones booleanas que habilitan o deshabilitan una característica o un comportamiento, y las opciones que requieren un valor o una estructura de tipo entero. Para habilitar una opción booleana, *lpOptionValue* señala a un entero distinto de cero. Para deshabilitar la opción *lpOptionValue* apunta a un entero igual a cero. *nOptionLen* debe ser igual a `sizeof(BOOL)` para las opciones booleanas. Para otras opciones, *lpOptionValue* apunta al entero o la estructura que contiene el valor deseado para la opción y *nOptionLen* es la longitud de la estructura o el entero.

SO_LINGER controla la acción realizada cuando los datos no enviados se ponen en cola en un socket `Close` y se llama a la función para cerrar el socket.

De forma predeterminada, no se puede enlazar un socket (vea [BIND](#bind)) a una dirección local que ya está en uso. Sin embargo, en ocasiones puede ser deseable "reutilizar" una dirección de esta manera. Puesto que todas las conexiones se identifican de forma única mediante la combinación de direcciones locales y remotas, no hay ningún problema con la conexión de dos sockets a la misma dirección local, siempre y cuando las direcciones remotas sean diferentes.

Para informar a la implementación de Windows Sockets `Bind` de que una llamada en un socket no debe estar deshabilitada porque otro socket ya está usando la dirección deseada, la aplicación debe establecer la opción de socket SO_REUSEADDR para el socket antes de emitir el `Bind` llame a. Tenga en cuenta que la opción se interpreta solo en el momento `Bind` de la llamada: por lo tanto, no es necesario (pero inocua) establecer la opción en un socket que no se va a enlazar a una dirección existente y establecer o restablecer `Bind` la opción después de que la llamada tenga ningún efecto en este u otro socket.

Una aplicación puede solicitar que la implementación de Windows Sockets habilite el uso de paquetes "Keep-Alive" en las conexiones del Protocolo de control de transmisión (TCP) activando la opción de socket SO_KEEPALIVE. Una implementación de Windows Sockets no necesita admitir el uso de Keep-alives: si lo hace, la semántica precisa es específica de la implementación, pero debe ajustarse a la sección 4.2.3.6 de RFC 1122: "Requisitos para hosts de Internet: capas de comunicación". Si se quita una conexión como resultado de "Keep-alives", se devuelve el código de error WSAENETRESET a cualquier llamada en curso en el socket, y las llamadas posteriores producirán un error con WSAENOTCONN.

La opción TCP_NODELAY deshabilita el algoritmo de Nagle. El algoritmo de Nagle se usa para reducir el número de paquetes pequeños que envía un host mediante el almacenamiento en búfer de datos de envío no confirmados hasta que se pueda enviar un paquete de tamaño completo. Sin embargo, para algunas aplicaciones este algoritmo puede impedir el rendimiento y se puede usar TCP_NODELAY para desactivarla. Los escritores de aplicaciones no deben establecer TCP_NODELAY a menos que el impacto de hacerlo sea bien entendido y deseado, ya que establecer TCP_NODELAY puede tener un impacto negativo significativo en el rendimiento de la red. TCP_NODELAY es la única opción de socket admitida que usa LEVEL IPPROTO_TCP; todas las demás opciones usan el nivel SOL_SOCKET.

Algunas implementaciones de Windows Sockets proporcionan información de depuración de salida si la opción SO_DEBUG está establecida por una aplicación.

Se admiten las siguientes opciones `SetSockOpt`para. El tipo identifica el tipo de datos direccionados por *lpOptionValue*.

|Valor|Type|Significado|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Permite la transmisión de mensajes de difusión en el socket.|
|SO_DEBUG|BOOL|Registra información de depuración.|
|SO_DONTLINGER|BOOL|No bloquee `Close` la espera de que se envíen datos no enviados. Establecer esta opción equivale a establecer SO_LINGER con `l_onoff` establecido en cero.|
|SO_DONTROUTE|BOOL|No enrutar: enviar directamente a la interfaz.|
|SO_KEEPALIVE|BOOL|Enviar conexiones persistentes.|
|SO_LINGER|`struct LINGER`|Permanencia en `Close` si hay datos no enviados.|
|SO_OOBINLINE|BOOL|Recibir datos fuera de banda en el flujo de datos normal.|
|SO_RCVBUF|**int**|Especifique el tamaño de búfer para las recepciones.|
|SO_REUSEADDR|BOOL|Permite enlazar el socket a una dirección que ya está en uso. (Vea [BIND](#bind)).|
|SO_SNDBUF|**int**|Especifique el tamaño de búfer para los envíos.|
|TCP_NODELAY|BOOL|Deshabilita el algoritmo de Nagle para la fusión de envíos.|

Las opciones de distribución de software Berkeley (BSD) `SetSockOpt` no compatibles con son:

|Valor|Type|Significado|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|El socket está escuchando|
|SO_ERROR|**int**|Obtiene el estado de error y borra.|
|SO_RCVLOWAT|**int**|Recibir una marca de límite inferior.|
|SO_RCVTIMEO|**int**|Tiempo de espera de recepción|
|SO_SNDLOWAT|**int**|Enviar marca de límite inferior.|
|SO_SNDTIMEO|**int**|Tiempo de espera de envío.|
|SO_TYPE|**int**|Tipo del socket.|
|IP_OPTIONS||Establezca el campo opciones en el encabezado IP.|

##  <a name="shutdown"></a>  CAsyncSocket::ShutDown

Llame a esta función miembro para deshabilitar los envíos, recepciones o ambos en el socket.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parámetros

*nHow*<br/>
Una marca que describe qué tipos de operación ya no se permitirán mediante los siguientes valores enumerados:

- **recibe = 0**

- **envíos = 1**

- **ambos = 2**

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED se debe producir una [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcta antes de usar esta API.

- WSAENETDOWN la implementación de Windows Sockets detectó un error en el subsistema de red.

- WSAEINVAL *nHow* no es válido.

- WSAEINPROGRESS está en curso una operación de bloqueo de Windows Sockets.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

`ShutDown`se utiliza en todos los tipos de sockets para deshabilitar la recepción, la transmisión o ambos. Si *nHow* es 0, no se permitirán las recepciones posteriores en el socket. Esto no tiene ningún efecto en las capas de protocolo inferiores.

En el protocolo de control de transmisión (TCP), la ventana TCP no cambia y los datos entrantes se aceptarán (pero no se confirmarán) hasta que se agote la ventana. En el protocolo de datagramas de usuario (UDP), los datagramas entrantes se aceptan y se ponen en cola. En ningún caso se generará un paquete de errores de ICMP. Si *nHow* es 1, no se permiten los envíos posteriores. En el caso de los Sockets TCP, se enviará un FIN. Al establecer *nHow* en 2, se deshabilitan los envíos y las recepciones como se describió anteriormente.

Tenga en `ShutDown` cuenta que no cierra el socket y que los recursos asociados al socket no se liberarán hasta `Close` que se llame a. Una aplicación no debe basarse en la posibilidad de reutilizar un socket una vez que se ha cerrado. En concreto, no se necesita una implementación de Windows Sockets para admitir el uso `Connect` de en este tipo de socket.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket:: alreceive](#onreceive).

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

*nSocketType*<br/>
Especifica `SOCK_STREAM` o `SOCK_DGRAM`.

*lEvent*<br/>
Máscara de red que especifica una combinación de eventos de red en los que la aplicación está interesada.

- `FD_READ`: Desea recibir notificaciones de preparación para la lectura.

- `FD_WRITE`: Desea recibir notificaciones de preparación para la escritura.

- `FD_OOB`: Desea recibir una notificación de la llegada de datos fuera de banda.

- `FD_ACCEPT`: Desea recibir una notificación de las conexiones entrantes.

- `FD_CONNECT`: Desea recibir una notificación de la conexión completada.

- `FD_CLOSE`: Desea recibir una notificación de cierre del socket.

*nProtocolType*<br/>
Protocolo que se va a usar con el socket específico de la familia de direcciones indicada.

*nAddressFormat*<br/>
Especificación de la familia de direcciones.

### <a name="return-value"></a>Valor devuelto

Devuelve `TRUE` si la operación se realiza correctamente; de lo contrario, devuelve `FALSE`.

### <a name="remarks"></a>Comentarios

Este método asigna un identificador de socket. No llama a [CAsyncSocket:: Bind](#bind) para enlazar el socket a una dirección especificada, por lo que debe llamar `Bind` a más adelante para enlazar el socket a una dirección especificada. Puede usar [CAsyncSocket::](#setsockopt) el valor de la opción socket antes de enlazarse.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
