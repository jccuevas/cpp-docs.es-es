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
ms.openlocfilehash: e384be534bdbb355554c28383e9e214e9084f217
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753031"
---
# <a name="casyncsocket-class"></a>CAsyncSocket (clase)

Representa un Socket de Windows: un extremo de la comunicación de red.

## <a name="syntax"></a>Sintaxis

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Construye un objeto `CAsyncSocket`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncSocket::Accept](#accept)|Acepta una conexión en el socket.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Solicita una notificación de eventos para el socket.|
|[CAsyncSocket::Attach](#attach)|Asocia un identificador de `CAsyncSocket` socket a un objeto.|
|[CAsyncSocket::Bind](#bind)|Asocia una dirección local con el socket.|
|[CAsyncSocket::Cerrar](#close)|Cierra el zócalo.|
|[CAsyncSocket::Connect](#connect)|Establece una conexión a un socket del mismo nivel.|
|[CAsyncSocket::Create](#create)|Crea un socket.|
|[CAsyncSocket::Detach](#detach)|Separa un identificador de `CAsyncSocket` socket de un objeto.|
|[CAsyncSocket::FromHandle](#fromhandle)|Devuelve un puntero `CAsyncSocket` a un objeto, dado un identificador de socket.|
|[CAsyncSocket::GetLastError](#getlasterror)|Obtiene el estado de error de la última operación que ha fallado.|
|[CAsyncSocket::GetPeerName](#getpeername)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket (controla las direcciones IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Obtiene el nombre local de un socket.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtiene el nombre local de un socket (controla las direcciones IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Recupera una opción de socket.|
|[CAsyncSocket::IOCtl](#ioctl)|Controla el modo del socket.|
|[CAsyncSocket::Escuchar](#listen)|Establece un socket para escuchar las solicitudes de conexión entrantes.|
|[CAsyncSocket::Receive](#receive)|Recibe datos del socket.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Recibe un datagrama y almacena la dirección de origen.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Recibe un datagrama y almacena la dirección de origen (controla las direcciones IPv6).|
|[CAsyncSocket::Enviar](#send)|Envía datos a un socket conectado.|
|[CAsyncSocket::SendTo](#sendto)|Envía datos a un destino específico.|
|[CAsyncSocket::SendToEx](#sendtoex)|Envía datos a un destino específico (controla direcciones IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Establece una opción de socket.|
|[CAsyncSocket::ShutDown](#shutdown)|Deshabilita `Send` y/o `Receive` llama al socket.|
|[CASyncSocket::Socket](#socket)|Asigna un identificador de socket.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Notifica a un socket de escucha que puede `Accept`aceptar solicitudes de conexión pendientes llamando a .|
|[CAsyncSocket::OnClose](#onclose)|Notifica a un socket que el socket conectado a él se ha cerrado.|
|[CAsyncSocket::OnConnect](#onconnect)|Notifica a un socket de conexión que el intento de conexión se ha completado, ya sea correctamente o por error.|
|[CAsyncSocket::OnOutofBandData](#onoutofbanddata)|Notifica a un socket receptor que hay datos fuera de banda que se leerán en el socket, normalmente un mensaje urgente.|
|[CAsyncSocket::OnReceive](#onreceive)|Notifica a un socket de escucha que hay `Receive`datos que se van a recuperar llamando a .|
|[CAsyncSocket::OnSend](#onsend)|Notifica a un socket que puede `Send`enviar datos llamando a .|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncSocket::operador ?](#operator_eq)|Asigna un nuevo valor `CAsyncSocket` a un objeto.|
|[CAsyncSocket::operador SOCKET](#operator_socket)|Utilice este operador para recuperar `CAsyncSocket` el identificador SOCKET del objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indica el identificador SOCKET `CAsyncSocket` asociado a este objeto.|

## <a name="remarks"></a>Observaciones

Clase `CAsyncSocket` encapsula la API de funciones de socket de Windows, proporcionando una abstracción orientada a objetos para los programadores que desean usar Windows Sockets junto con MFC.

Esta clase se basa en la suposición de que entiende las comunicaciones de red. Usted es responsable de controlar el bloqueo, las diferencias de orden de bytes y las conversiones entre cadenas Unicode y de conjunto de caracteres multibyte (MBCS). Si desea una interfaz más cómoda que administre estos problemas por usted, vea la clase [CSocket](../../mfc/reference/csocket-class.md).

Para usar `CAsyncSocket` un objeto, llame a su constructor y, a continuación, llame a la [función Create](#create) para crear el identificador de socket subyacente (tipo `SOCKET`), excepto en sockets aceptados. Para un socket de servidor llame a la [escuchar](#listen) función miembro y para un socket de cliente llame a la [Connect](#connect) función miembro. El socket de servidor debe llamar a la función [Accept](#accept) al recibir una solicitud de conexión. Utilice las `CAsyncSocket` funciones restantes para realizar comunicaciones entre sockets. Al finalizar, `CAsyncSocket` destruya el objeto si se creó en el montón; el destructor llama automáticamente a la función [Cerrar.](#close) El tipo de datos SOCKET se describe en el artículo [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

> [!NOTE]
> Al usar sockets MFC en subprocesos secundarios en una `AfxSocketInit` aplicación MFC vinculada estáticamente, debe llamar a cada subproceso que usa sockets para inicializar las bibliotecas de sockets. De forma `AfxSocketInit` predeterminada, solo se llama en el subproceso principal.

Para obtener más información, vea [Windows Sockets: Using Class CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) and related articles., así como [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket::Accept

Llame a esta función miembro para aceptar una conexión en un socket.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parámetros

*rConnectedSocket*<br/>
Una referencia que identifica un nuevo socket que está disponible para la conexión.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que recibe la dirección del socket de conexión, como se conoce en la red. El formato exacto del argumento *lpSockAddr* viene determinado por la familia de direcciones establecida cuando se creó el socket. Si *lpSockAddr* y/o *lpSockAddrLen* son iguales a NULL, no se devuelve ninguna información sobre la dirección remota del socket aceptado.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección en *lpSockAddr* en bytes. El *lpSockAddrLen* es un parámetro valor-resultado: debe contener inicialmente la cantidad de espacio a la que apunta *lpSockAddr*; en la devolución contendrá la longitud real (en bytes) de la dirección devuelta.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* es demasiado pequeño (menos que el tamaño de una estructura [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Una llamada de bloqueo de Windows Sockets está en curso.

- WSAEINVAL `Listen` no se invocó antes de aceptar.

- WSAEMFILE La cola está vacía a la entrada para aceptar y no hay descriptores disponibles.

- WSAENOBUFS No hay espacio de búfer disponible.

- WSAENOTSOCK El descriptor no es un socket.

- WSAEOPNOTSUPP El socket al que se hace referencia no es un tipo que admita el servicio orientado a la conexión.

- WSAEWOULDBLOCK El socket se marca como no bloqueante y no hay conexiones presentes para ser aceptadas.

### <a name="remarks"></a>Observaciones

Esta rutina extrae la primera conexión en la cola de conexiones pendientes, crea un nuevo socket con las mismas propiedades que este socket y lo adjunta a *rConnectedSocket*. Si no hay conexiones pendientes en la cola, `Accept` devuelve cero y `GetLastError` devuelve un error. El socket aceptado ( *rConnectedSocket)* no se puede utilizar para aceptar más conexiones. El socket original permanece abierto y escuchando.

El argumento *lpSockAddr* es un parámetro de resultado que se rellena con la dirección del socket de conexión, como se conoce a la capa de comunicaciones. `Accept`se utiliza con tipos de socket basados en conexiones, como SOCK_STREAM.

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect

Llame a esta función miembro para solicitar la notificación de eventos para un socket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parámetros

*Levent*<br/>
Una máscara de bits que especifica una combinación de eventos de red en los que la aplicación está interesada.

- FD_READ Desea recibir una notificación de preparación para la lectura.

- FD_WRITE Desea recibir una notificación cuando los datos estén disponibles para ser leídos.

- FD_OOB Desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT Desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT Desea recibir una notificación de los resultados de la conexión.

- FD_CLOSE Desea recibir una notificación cuando un socket ha sido cerrado por un par.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEINVAL Indica que uno de los parámetros especificados no era válido.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

### <a name="remarks"></a>Observaciones

Esta función se utiliza para especificar qué funciones de notificación de devolución de llamada MFC se llamará para el socket. `AsyncSelect`automáticamente establece este socket en modo de no bloqueo. Para obtener más información, vea el artículo [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Attach

Llame a esta función miembro para `CAsyncSocket` asociar el identificador *hSocket* a un objeto.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

*Levent*<br/>
Una máscara de bits que especifica una combinación de eventos de red en los que la aplicación está interesada.

- FD_READ Desea recibir una notificación de preparación para la lectura.

- FD_WRITE Desea recibir una notificación cuando los datos estén disponibles para ser leídos.

- FD_OOB Desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT Desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT Desea recibir una notificación de los resultados de la conexión.

- FD_CLOSE Desea recibir una notificación cuando un socket ha sido cerrado por un par.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente.

### <a name="remarks"></a>Observaciones

El identificador SOCKET se almacena en el miembro de datos [m_hSocket](#m_hsocket) del objeto.

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Bind

Llame a esta función miembro para asociar una dirección local con el socket.

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
La dirección de red, un número punteado como "128.56.22.8". Pasar la cadena NULL para `CAsyncSocket` este parámetro indica que la instancia debe escuchar la actividad del cliente en todas las interfaces de red.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección que se va a asignar a este socket.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). En la lista siguiente se tratan algunos de los errores que se pueden devolver. Para obtener una lista completa, vea [Códigos](/windows/win32/winsock/windows-sockets-error-codes-2)de error de Windows Sockets .

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEADDRINUSE La dirección especificada ya está en uso. (Consulte la opción de socket SO_REUSEADDR en [SetSockOpt](#setsockopt).)

- WSAEFAULT El *argumento nSockAddrLen* es demasiado pequeño (menos que el tamaño de una estructura [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Una llamada de bloqueo de Windows Sockets está en curso.

- WSAEAFNOSUPPORT Este puerto no admite la familia de direcciones especificada.

- WSAEINVAL El socket ya está enlazado a una dirección.

- WSAENOBUFS No hay suficientes búferes disponibles, demasiadas conexiones.

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

Esta rutina se utiliza en un datagrama `Connect` no `Listen` conectado o un socket de secuencia, antes de las llamadas posteriores o. Antes de que pueda aceptar solicitudes de conexión, un socket de servidor `Bind`de escucha debe seleccionar un número de puerto y darlo a conocer a Windows Sockets llamando a . `Bind`establece la asociación local (dirección de host/número de puerto) del socket asignando un nombre local a un socket sin nombre.

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket

Construye un objeto de socket en blanco.

```
CAsyncSocket();
```

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a su `Create` función miembro para crear la estructura de datos SOCKET y enlazar su dirección. (En el lado del servidor de una comunicación de Windows `Accept` Sockets, cuando el `Create` socket de escucha crea un socket para usar en la llamada, no se llama a ese socket.)

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Cerrar

Cierra el zócalo.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Esta función libera el descriptor de socket para que se produzcaun un error en otras referencias a él con el error WSAENOTSOCK. Si se trata de la última referencia al socket subyacente, se descartan la información de nomenclatura asociada y los datos en cola. El destructor del objeto `Close` socket le llama.

Para `CAsyncSocket`, pero `CSocket`no para `Close` , la semántica de se ven afectadas por las opciones de socket SO_LINGER y SO_DONTLINGER. Para obtener más información, consulte la función `GetSockOpt`miembro .

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket::Connect

Llame a esta función miembro para establecer una conexión a una secuencia no conectada o un socket de datagrama.

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
La dirección de red del socket al que está conectado este objeto: un nombre de equipo como "ftp.microsoft.com", o un número punteado como "128.56.22.8".

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección del socket conectado.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Si esto indica un código de error de WSAEWOULDBLOCK y la aplicación está utilizando las devoluciones de llamada reemplazables, la aplicación recibirá un `OnConnect` mensaje cuando se complete la operación de conexión. Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEADDRINUSE La dirección especificada ya está en uso.

- WSAEINPROGRESS Una llamada de bloqueo de Windows Sockets está en curso.

- WSAEADDRNOTAVAIL La dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden utilizar con este socket.

- WSAECONNREFUSED Se ha rechazado el intento de conexión.

- WSAEDESTADDRREQ Se requiere una dirección de destino.

- WSAEFAULT El argumento *nSockAddrLen* es incorrecto.

- WSAEINVAL Dirección de host no válida.

- WSAEISCONN El socket ya está conectado.

- WSAEMFILE No hay más descriptores de archivo disponibles.

- WSAENETUNREACH La red no se puede alcanzar desde este host en este momento.

- WSAENOBUFS No hay espacio de búfer disponible. El zócalo no se puede conectar.

- WSAENOTSOCK El descriptor no es un socket.

- WSAETIMEDOUT Intento de conectar el tiempo de espera sin establecer una conexión.

- WSAEWOULDBLOCK El socket se marca como no bloqueante y la conexión no se puede completar inmediatamente.

### <a name="remarks"></a>Observaciones

Si el socket no está enlazado, el sistema asigna valores únicos a la asociación local y el socket se marca como enlazado. Tenga en cuenta que si el campo de `Connect` dirección de la estructura de nombre es todos ceros, devolverá cero. Para obtener información de `GetLastError` error extendida, llame a la función miembro.

Para sockets de secuencia (tipo SOCK_STREAM), se inicia una conexión activa con el host externo. Cuando la llamada de socket se completa correctamente, el socket está listo para enviar/recibir datos.

Para un socket de datagrama (tipo SOCK_DGRAM), se establece `Send` `Receive` un destino predeterminado, que se usará en las llamadas posteriores y.

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Create

Llame `Create` a la función miembro después de construir un objeto de socket para crear el socket de Windows y adjuntarlo.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
Un puerto conocido que se usará con el socket, o 0 si desea que Windows Sockets seleccione un puerto.

*nSocketType*<br/>
SOCK_STREAM o SOCK_DGRAM.

*Levent*<br/>
Una máscara de bits que especifica una combinación de eventos de red en los que la aplicación está interesada.

- FD_READ Desea recibir una notificación de preparación para la lectura.

- FD_WRITE Desea recibir una notificación de preparación para escribir.

- FD_OOB Desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT Desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT Desea recibir una notificación de conexión completada.

- FD_CLOSE Desea recibir una notificación de cierre de socket.

*lpszSockAddress*<br/>
Un puntero a una cadena que contiene la dirección de red del socket conectado, un número punteado como "128.56.22.8". Pasar la cadena NULL para `CAsyncSocket` este parámetro indica que la instancia debe escuchar la actividad del cliente en todas las interfaces de red.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEAFNOSUPPORT No se admite la familia de direcciones especificada.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEMFILE No hay más descriptores de archivo disponibles.

- WSAENOBUFS No hay espacio de búfer disponible. No se puede crear el socket.

- WSAEPROTONOSUPPORT No se admite el puerto especificado.

- WSAEPROTOTYPE El puerto especificado es el tipo incorrecto para este socket.

- WSAESOCKTNOSUPPORT El tipo de socket especificado no se admite en esta familia de direcciones.

### <a name="remarks"></a>Observaciones

`Create`llama a [Socket](#socket) y, si se realiza correctamente, llama a [Bind](#bind) para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:

- SOCK_STREAM Proporciona secuencias de bytes secuenciadas, fiables, dúplex completo y basadas en conexiones. Utiliza el Protocolo de control de transmisión (TCP) para la familia de direcciones de Internet.

- SOCK_DGRAM Admite datagramas, que son paquetes sin conexión y poco fiables de una longitud máxima fija (normalmente pequeña). Utiliza el Protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet.

    > [!NOTE]
    >  La `Accept` función miembro toma una `CSocket` referencia a un nuevo objeto vacío como parámetro. Debe construir este objeto `Accept`antes de llamar a . Tenga en cuenta que si este objeto de socket sale del ámbito, la conexión se cierra. No llame `Create` a este nuevo objeto de socket.

> [!IMPORTANT]
> `Create`**no** es seguro para subprocesos.  Si lo está llamando en un entorno multiproceso donde podría ser invocado simultáneamente por diferentes subprocesos, asegúrese de proteger cada llamada con una exclusión mutua u otro bloqueo de sincronización.

Para obtener más información acerca de los sockets de flujo y datagrama, vea los artículos [Windows Sockets: Background](../../mfc/windows-sockets-background.md) y [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md) y Windows Sockets 2 [API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach

Llame a esta función miembro para separar el `CAsyncSocket` identificador SOCKET en el *m_hSocket* miembro de datos del objeto y establecer *m_hSocket* null.

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::FromHandle

Devuelve un puntero `CAsyncSocket` a un objeto.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

### <a name="return-value"></a>Valor devuelto

Un puntero `CAsyncSocket` a un objeto, o `CAsyncSocket` NULL si no hay ningún objeto asociado a *hSocket*.

### <a name="remarks"></a>Observaciones

Cuando se le da `CAsyncSocket` un identificador SOCKET, si un objeto no está asociado al identificador, la función miembro devuelve NULL.

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError

Llame a esta función miembro para obtener el estado de error para la última operación que produjo un error.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto indica el código de error para la última rutina de LA API de Windows Sockets realizada por este subproceso.

### <a name="remarks"></a>Observaciones

Cuando una función miembro determinada indica `GetLastError` que se ha producido un error, debe llamarse para recuperar el código de error adecuado. Consulte las descripciones de la función miembro individuales para obtener una lista de los códigos de error aplicables.

Para obtener más información acerca de los códigos de error, vea API de [Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName

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
Referencia a `CString` un objeto que recibe una dirección IP de número punteado.

*rPeerPort*<br/>
Referencia a un UINT que almacena un puerto.

*lpSockAddr*<br/>
Puntero a la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que recibe el nombre del socket del mismo nivel.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección en *lpSockAddr* en bytes. A la vuelta, el argumento *lpSockAddrLen* contiene el tamaño real de *lpSockAddr* devuelto en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* no es lo suficientemente grande.

- WSAEINPROGRESS Una llamada de bloqueo de Windows Sockets está en curso.

- WSAENOTCONN El socket no está conectado.

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

Para controlar direcciones IPv6, utilice [CAsyncSocket::GetPeerNameEx](#getpeernameex).

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx

Llame a esta función miembro para obtener la dirección del socket del mismo nivel al que está conectado este socket (controla las direcciones IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parámetros

*rPeerAddress*<br/>
Referencia a `CString` un objeto que recibe una dirección IP de número punteado.

*rPeerPort*<br/>
Referencia a un UINT que almacena un puerto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* no es lo suficientemente grande.

- WSAEINPROGRESS Una llamada de bloqueo de Windows Sockets está en curso.

- WSAENOTCONN El socket no está conectado.

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

Esta función es la misma que [CAsyncSocket::GetPeerName](#getpeername) excepto que controla direcciones IPv6, así como protocolos más antiguos.

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName

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
Referencia a `CString` un objeto que recibe una dirección IP de número punteado.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que recibe la dirección del socket.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* no es lo suficientemente grande.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAENOTSOCK El descriptor no es un socket.

- WSAEINVAL El socket no se ha `Bind`enlazado a una dirección con .

### <a name="remarks"></a>Observaciones

Esta llamada es especialmente `Connect` útil cuando se `Bind` ha realizado una llamada sin hacer una primera; esta llamada proporciona el único medio por el cual usted puede determinar la asociación local que ha sido fijada por el sistema.

Para controlar direcciones IPv6, utilice [CAsyncSocket::GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx

Llame a esta función miembro para obtener el nombre local de un socket (controla las direcciones IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parámetros

*rSocketAddress*<br/>
Referencia a `CString` un objeto que recibe una dirección IP de número punteado.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* no es lo suficientemente grande.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAENOTSOCK El descriptor no es un socket.

- WSAEINVAL El socket no se ha `Bind`enlazado a una dirección con .

### <a name="remarks"></a>Observaciones

Esta llamada es la misma que [CAsyncSocket::GetSockName](#getsockname) excepto que controla direcciones IPv6, así como protocolos más antiguos.

Esta llamada es especialmente `Connect` útil cuando se `Bind` ha realizado una llamada sin hacer una primera; esta llamada proporciona el único medio por el cual usted puede determinar la asociación local que ha sido fijada por el sistema.

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockOpt

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
La opción de socket para la que se va a recuperar el valor.

*lpOptionValue*<br/>
Puntero al búfer en el que se va a devolver el valor de la opción solicitada. El valor asociado a la opción seleccionada se devuelve en el búfer *lpOptionValue*. El entero al que apunta *lpOptionLen* debe contener originalmente el tamaño de este búfer en bytes; y a la vuelta, se establecerá en el tamaño del valor devuelto. Por SO_LINGER, este será el `LINGER` tamaño de una estructura; para todas las demás opciones será del tamaño de un BOOL o un **int,** dependiendo de la opción. Consulte la lista de opciones y sus tamaños en la sección Comentarios.

*lpOptionLen*<br/>
Puntero al tamaño del búfer *lpOptionValue* en bytes.

*nNivel*<br/>
El nivel en el que se define la opción; los únicos niveles admitidos son SOL_SOCKET y IPPROTO_TCP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Si nunca se `SetSockOpt`estableció `GetSockOpt` una opción con , devuelve el valor predeterminado de la opción. Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpOptionLen* no era válido.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAENOPROTOOPT La opción es desconocida o no es compatible. En particular, SO_BROADCAST no se admite en sockets de tipo SOCK_STREAM, mientras que SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER y SO_OOBINLINE no se admiten en sockets de tipo SOCK_DGRAM.

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

`GetSockOpt`recupera el valor actual de una opción de socket asociada a un socket de cualquier tipo, en cualquier estado, y almacena el resultado en *lpOptionValue*. Las opciones afectan a las operaciones de socket, como el enrutamiento de paquetes, la transferencia de datos fuera de banda, etc.

Las siguientes opciones `GetSockOpt`son compatibles con . El type identifica el tipo de datos direccionados por *lpOptionValue*. La opción TCP_NODELAY utiliza IPPROTO_TCP de nivel; todas las demás opciones utilizan el nivel SOL_SOCKET.

|Value|Tipo|Significado|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|El enchufe está escuchando.|
|SO_BROADCAST|BOOL|El socket está configurado para la transmisión de mensajes de difusión.|
|SO_DEBUG|BOOL|La depuración está habilitada.|
|SO_DONTLINGER|BOOL|Si es true, la opción SO_LINGER está deshabilitada.|
|SO_DONTROUTE|BOOL|El enrutamiento está deshabilitado.|
|SO_ERROR|**int**|Recuperar el estado del error y borrar.|
|SO_KEEPALIVE|BOOL|Se están enviando vidas de keepalives.|
|SO_LINGER|`struct LINGER`|Devuelve las opciones de linger actuales.|
|SO_OOBINLINE|BOOL|Los datos fuera de banda se reciben en el flujo de datos normal.|
|SO_RCVBUF|int|Tamaño del búfer para las recepcións.|
|SO_REUSEADDR|BOOL|El socket se puede enlazar a una dirección que ya está en uso.|
|SO_SNDBUF|**int**|Tamaño del búfer para los envíos.|
|SO_TYPE|**int**|El tipo del socket (por ejemplo, SOCK_STREAM).|
|TCP_NODELAY|BOOL|Deshabilita el algoritmo de Nagle para la fusión de envíos.|

Las opciones de Berkeley Software `GetSockOpt` Distribution (BSD) no compatibles son:

|Value|Tipo|Significado|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Reciba una marca de agua baja.|
|SO_RCVTIMEO|**int**|Tiempo de espera de recepción.|
|SO_SNDLOWAT|**int**|Envíe una marca de agua baja.|
|SO_SNDTIMEO|**int**|Enviar tiempo de espera.|
|IP_OPTIONS||Obtenga opciones en el encabezado IP.|
|TCP_MAXSEG|**int**|Obtenga el tamaño máximo del segmento TCP.|

Llamar `GetSockOpt` con una opción no admitida dará lugar a un código de `GetLastError`error de WSAENOPROTOOPT que se devuelve desde .

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl

Llame a esta función miembro para controlar el modo de un socket.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parámetros

*lCommand*<br/>
El comando que se debe realizar en el socket.

*lpArgument*<br/>
Un puntero a un parámetro para *lCommand*.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEINVAL *lCommand* no es un comando válido, o *lpArgument* no es un parámetro aceptable para *lCommand*, o el comando no es aplicable al tipo de socket proporcionado.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

Esta rutina se puede utilizar en cualquier socket en cualquier estado. Se utiliza para obtener o recuperar los parámetros operativos asociados con el socket, independientemente del protocolo y el subsistema de comunicaciones. Se admiten los siguientes comandos:

- FIONBIO Activar o desactivar el modo de no bloqueo en el socket. El parámetro *lpArgument* `DWORD`apunta a un , que es distinto de cero si se va a habilitar el modo de no bloqueo y cero si se va a deshabilitar. Si `AsyncSelect` se ha emitido en un socket, después cualquier intento de utilizar `IOCtl` para fijar el socket de nuevo al modo de bloqueo fallará con WSAEINVAL. Para volver a establecer el socket en modo de bloqueo y evitar `AsyncSelect` el `AsyncSelect` error WSAEINVAL, una `IOCtl`aplicación debe deshabilitarprimero primero llamando con el parámetro *lEvent* igual a 0 y, a continuación, llame a .

- FIONREAD Determine el número máximo de bytes `Receive` que se pueden leer con una llamada de este socket. El parámetro *lpArgument* `DWORD` apunta `IOCtl` a un lugar en el que almacena el resultado. Si este socket es de tipo SOCK_STREAM, FIONREAD devuelve la cantidad `Receive`total de datos que se pueden leer en un solo ; esto es normalmente el mismo que la cantidad total de datos en cola en el socket. Si este socket es de tipo SOCK_DGRAM, FIONREAD devuelve el tamaño del primer datagrama en cola en el socket.

- SIOCATMARK Determine si se han leído todos los datos fuera de banda. Esto solo se aplica a un socket de tipo SOCK_STREAM que se ha configurado para la recepción en línea de cualquier dato fuera de banda (SO_OOBINLINE). Si no hay datos fuera de banda esperando para ser leídos, la operación devuelve distinto de cero. De lo contrario, devuelve `Receive` `ReceiveFrom` 0, y el siguiente o realizado en el socket recuperará algunos o todos los datos que preceden a la "marca"; la aplicación debe utilizar la operación SIOCATMARK para determinar si quedan datos. Si hay datos normales que preceden a los datos "urgentes" (fuera de banda), se recibirán en orden. (Tenga en `Receive` `ReceiveFrom` cuenta que un o nunca mezclará datos fuera de banda y normales en la misma llamada.) El parámetro *lpArgument* `DWORD` apunta `IOCtl` a un lugar en el que almacena el resultado.

Esta función es `ioctl()` un subconjunto de como se utiliza en los sockets de Berkeley. En particular, no hay ningún comando que sea equivalente a FIOASYNC, mientras que SIOCATMARK es el único comando socket-level que se soporta.

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket::Escuchar

Llame a esta función miembro para escuchar las solicitudes de conexión entrantes.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parámetros

*nConnectionBacklog*<br/>
La longitud máxima a la que puede crecer la cola de conexiones pendientes. El rango válido es de 1 a 5.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEADDRINUSE Se ha intentado escuchar una dirección en uso.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEINVAL El socket no `Bind` se ha enlazado o ya está conectado.

- WSAEISCONN El socket ya está conectado.

- WSAEMFILE No hay más descriptores de archivo disponibles.

- WSAENOBUFS No hay espacio de búfer disponible.

- WSAENOTSOCK El descriptor no es un socket.

- WSAEOPNOTSUPP El socket al que se `Listen` hace referencia no es de un tipo que admita la operación.

### <a name="remarks"></a>Observaciones

Para aceptar conexiones, el `Create`socket se crea primero con , `Listen`se especifica un trabajo `Accept`pendiente para las conexiones entrantes con , y, a continuación, se aceptan las conexiones con . `Listen`solo se aplica a los sockets que admiten conexiones, es decir, las de tipo SOCK_STREAM. Este socket se pone en modo "pasivo" donde las conexiones entrantes se reconocen y ponen en cola a la espera de la aceptación por el proceso.

Esta función suele ser utilizada por servidores (o cualquier aplicación que desee aceptar conexiones) que podrían tener más de una solicitud de conexión a la vez: si una solicitud de conexión llega con la cola llena, el cliente recibirá un error con una indicación de WSAECONNREFUSED.

`Listen`intenta seguir funcionando racionalmente cuando no hay puertos disponibles (descriptores). Aceptará conexiones hasta que se vacíe la cola. Si los puertos están `Listen` disponibles, una llamada posterior a o `Accept` rellenará la cola al "backlog" actual o más reciente, si es posible, y reanudará la escucha de las conexiones entrantes.

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket

Contiene el identificador SOCKET para el `CAsyncSocket` socket encapsulado por este objeto.

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAccept

Llamado por el marco de trabajo para notificar a un socket de escucha que puede aceptar solicitudes de conexión pendientes mediante una llamada a la [Accept](#accept) función miembro.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos `OnAccept` de error se aplican a la función miembro:

- **0** La función se ha ejecutado correctamente.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose

Llamado por el marco de trabajo para notificar a este socket que el socket conectado está cerrado por su proceso.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos `OnClose` de error se aplican a la función miembro:

- **0** La función se ha ejecutado correctamente.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAECONNRESET La conexión fue restablecido por el lado remoto.

- WSAECONNABORTED La conexión se ha anulado debido al tiempo de espera u otro error.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect

Llamado por el marco de trabajo para notificar a este socket de conexión que su intento de conexión se ha completado, ya sea correctamente o por error.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos `OnConnect` de error se aplican a la función miembro:

- **0** La función se ha ejecutado correctamente.

- WSAEADDRINUSE La dirección especificada ya está en uso.

- WSAEADDRNOTAVAIL La dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden utilizar con este socket.

- WSAECONNREFUSED El intento de conexión fue rechazado por la fuerza.

- WSAEDESTADDRREQ Se requiere una dirección de destino.

- WSAEFAULT El argumento *lpSockAddrLen* es incorrecto.

- WSAEINVAL El socket ya está enlazado a una dirección.

- WSAEISCONN El socket ya está conectado.

- WSAEMFILE No hay más descriptores de archivo disponibles.

- WSAENETUNREACH La red no se puede alcanzar desde este host en este momento.

- WSAENOBUFS No hay espacio de búfer disponible. El zócalo no se puede conectar.

- WSAENOTCONN El socket no está conectado.

- WSAENOTSOCK El descriptor es un archivo, no un socket.

- WSAETIMEDOUT El intento de conectar el tiempo de espera es espera sin establecer una conexión.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> En [CSocket](../../mfc/reference/csocket-class.md) `OnConnect` , nunca se llama a la función de notificación. Para las conexiones, simplemente llame a `Connect`, que se devolverá cuando se complete la conexión (ya sea correctamente o por error). Cómo se controlan las notificaciones de conexión es un detalle de implementación de MFC.

Para obtener más información, consulte [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutofBandData

Llamado por el marco de trabajo para notificar al socket de recepción que el socket de envío tiene datos fuera de banda para enviar.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos `OnOutOfBandData` de error se aplican a la función miembro:

- **0** La función se ha ejecutado correctamente.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

### <a name="remarks"></a>Observaciones

Los datos fuera de banda son un canal lógicamente independiente que está asociado a cada par de sockets conectados de tipo SOCK_STREAM. El canal se utiliza generalmente para enviar datos urgentes.

MFC admite datos fuera de banda, `CAsyncSocket` pero se desaconseja a los usuarios de clase usarlos. La forma más fácil es crear un segundo socket para pasar dichos datos. Para obtener más información acerca de los datos fuera de banda, vea [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive

Llamado por el marco de trabajo para notificar a este socket que `Receive` hay datos en el búfer que se pueden recuperar mediante una llamada a la función miembro.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos `OnReceive` de error se aplican a la función miembro:

- **0** La función se ha ejecutado correctamente.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend

Llamado por el marco de trabajo para notificar al `Send` socket que ahora puede enviar datos mediante una llamada a la función miembro.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos `OnSend` de error se aplican a la función miembro:

- **0** La función se ha ejecutado correctamente.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::operador ?

Asigna un nuevo valor `CAsyncSocket` a un objeto.

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia a `CAsyncSocket` un objeto existente.

### <a name="remarks"></a>Observaciones

Llame a esta función para copiar un objeto existente `CAsyncSocket` en otro `CAsyncSocket` objeto.

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::operador SOCKET

Utilice este operador para recuperar `CAsyncSocket` el identificador SOCKET del objeto.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador del objeto SOCKET; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Puede usar el identificador para llamar a las API de Windows directamente.

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Receive

Llame a esta función miembro para recibir datos de un socket.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un búfer para los datos entrantes.

*nBufLen*<br/>
La longitud de *lpBuf* en bytes.

*nFlags*<br/>
Especifica la forma en que se realiza la llamada. La semántica de esta función viene determinada por las opciones de socket y el parámetro *nFlags.* Este último se construye combinando cualquiera de los siguientes valores con el operador **C++ OR:**

- MSG_PEEK echar un vistazo a los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- MSG_OOB Procesar datos fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si no se `Receive` produce ningún error, devuelve el número de bytes recibidos. Si la conexión se ha cerrado, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAENOTCONN El socket no está conectado.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAENOTSOCK El descriptor no es un socket.

- Se especificó MSG_OOB WSAEOPNOTSUPP, pero el socket no es de tipo SOCK_STREAM.

- WSAESHUTDOWN El socket se ha apagado; no es posible `Receive` llamar a `ShutDown` un socket después de que se ha invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK El socket se marca `Receive` como no bloqueante y la operación se bloquearía.

- WSAEMSGSIZE El datagrama era demasiado grande para caber en el búfer especificado y se truncó.

- WSAEINVAL El socket no `Bind`se ha enlazado con .

- WSAECONNABORTED El circuito virtual se anuló debido al tiempo de espera u otro error.

- WSAECONNRESET El circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Observaciones

Esta función se utiliza para sockets de flujo o datagrama conectados y se utiliza para leer los datos entrantes.

Para sockets de tipo SOCK_STREAM, se devuelve toda la información que esté disponible actualmente hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y los datos fuera de banda no se han leído, solo se devolverán los datos fuera de banda. La aplicación puede `IOCtlSIOCATMARK` usar la opción o [OnOutOfBandData](#onoutofbanddata) para determinar si queda que leer más datos fuera de banda.

Para los sockets de datagramas, los datos se extraen del primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con `Receive` la primera parte del datagrama, se pierde el exceso de datos y devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE. Si no hay datos entrantes disponibles en el socket, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. La función de devolución de llamada [OnReceive](#onreceive) se puede utilizar para determinar cuándo llegan más datos.

Si el socket es de tipo SOCK_STREAM y el lado `Receive` remoto ha apagado la conexión correctamente, un se completará inmediatamente con 0 bytes recibidos. Si se ha restablecido `Receive` la conexión, se producirá un error con el error WSAECONNRESET.

`Receive`debe llamarse solo una vez por cada vez [que cAsyncSocket::OnReceive](#onreceive) se llama.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::ReceiveFrom

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
Un búfer para los datos entrantes.

*nBufLen*<br/>
La longitud de *lpBuf* en bytes.

*rSocketAddress*<br/>
Referencia a `CString` un objeto que recibe una dirección IP de número punteado.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección de origen al devolverla.

*lpSockAddrLen*<br/>
Puntero a la longitud de la dirección de origen en *lpSockAddr* en bytes.

*nFlags*<br/>
Especifica la forma en que se realiza la llamada. La semántica de esta función viene determinada por las opciones de socket y el parámetro *nFlags.* Este último se construye combinando cualquiera de los siguientes valores con el operador **C++ OR:**

- MSG_PEEK echar un vistazo a los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- MSG_OOB Procesar datos fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si no se `ReceiveFrom` produce ningún error, devuelve el número de bytes recibidos. Si la conexión se ha cerrado, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y `GetLastError`se puede recuperar un código de error específico llamando a . Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* no era válido: el búfer *lpSockAddr* era demasiado pequeño para dar cabida a la dirección del mismo nivel.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEINVAL El socket no `Bind`se ha enlazado con .

- WSAENOTCONN El socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK El descriptor no es un socket.

- Se especificó MSG_OOB WSAEOPNOTSUPP, pero el socket no es de tipo SOCK_STREAM.

- WSAESHUTDOWN El socket se ha apagado; no es posible `ReceiveFrom` llamar a `ShutDown` un socket después de que se ha invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK El socket se marca `ReceiveFrom` como no bloqueante y la operación se bloquearía.

- WSAEMSGSIZE El datagrama era demasiado grande para caber en el búfer especificado y se truncó.

- WSAECONNABORTED El circuito virtual se anuló debido al tiempo de espera u otro error.

- WSAECONNRESET El circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Observaciones

Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.

Para controlar direcciones IPv6, utilice [CAsyncSocket::ReceiveFromEx](#receivefromex).

Para sockets de tipo SOCK_STREAM, se devuelve toda la información que esté disponible actualmente hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y los datos fuera de banda no se han leído, solo se devolverán los datos fuera de banda. La aplicación puede `IOCtlSIOCATMARK` utilizar `OnOutOfBandData` la opción o para determinar si quedan más datos fuera de banda por leer. Los *parámetros lpSockAddr* y *lpSockAddrLen* se omiten para los sockets de SOCK_STREAM.

Para los sockets de datagramas, los datos se extraen del primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con `ReceiveFrom` la primera parte del mensaje, se pierde el exceso de datos y devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE.

Si *lpSockAddr* es distinto de cero y el socket es de tipo SOCK_DGRAM, la dirección de red del socket que envió los datos se copia en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) correspondiente. El valor señalado por *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modifica al devolver para indicar el tamaño real de la dirección almacenada allí. Si no hay datos entrantes `ReceiveFrom` disponibles en el socket, la llamada espera a que lleguen los datos a menos que el socket no se bloquee. En este caso, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. La `OnReceive` devolución de llamada se puede utilizar para determinar cuándo llegan más datos.

Si el socket es de tipo SOCK_STREAM y el lado `ReceiveFrom` remoto ha apagado la conexión correctamente, un se completará inmediatamente con 0 bytes recibidos.

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx

Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) o en *rSocketAddress* (controla direcciones IPv6).

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
Un búfer para los datos entrantes.

*nBufLen*<br/>
La longitud de *lpBuf* en bytes.

*rSocketAddress*<br/>
Referencia a `CString` un objeto que recibe una dirección IP de número punteado.

*rSocketPort*<br/>
Referencia a un UINT que almacena un puerto.

*nFlags*<br/>
Especifica la forma en que se realiza la llamada. La semántica de esta función viene determinada por las opciones de socket y el parámetro *nFlags.* Este último se construye combinando cualquiera de los siguientes valores con el operador **C++ OR:**

- MSG_PEEK echar un vistazo a los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- MSG_OOB Procesar datos fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si no se `ReceiveFromEx` produce ningún error, devuelve el número de bytes recibidos. Si la conexión se ha cerrado, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y `GetLastError`se puede recuperar un código de error específico llamando a . Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT El argumento *lpSockAddrLen* no era válido: el búfer *lpSockAddr* era demasiado pequeño para dar cabida a la dirección del mismo nivel.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEINVAL El socket no `Bind`se ha enlazado con .

- WSAENOTCONN El socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK El descriptor no es un socket.

- Se especificó MSG_OOB WSAEOPNOTSUPP, pero el socket no es de tipo SOCK_STREAM.

- WSAESHUTDOWN El socket se ha apagado; no es posible `ReceiveFromEx` llamar a `ShutDown` un socket después de que se ha invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK El socket se marca `ReceiveFromEx` como no bloqueante y la operación se bloquearía.

- WSAEMSGSIZE El datagrama era demasiado grande para caber en el búfer especificado y se truncó.

- WSAECONNABORTED El circuito virtual se anuló debido al tiempo de espera u otro error.

- WSAECONNRESET El circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Observaciones

Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.

Esta función es la misma que [CAsyncSocket::ReceiveFrom](#receivefrom) excepto que controla direcciones IPv6, así como protocolos más antiguos.

Para sockets de tipo SOCK_STREAM, se devuelve toda la información que esté disponible actualmente hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y los datos fuera de banda no se han leído, solo se devolverán los datos fuera de banda. La aplicación puede `IOCtlSIOCATMARK` utilizar `OnOutOfBandData` la opción o para determinar si quedan más datos fuera de banda por leer. Los *parámetros lpSockAddr* y *lpSockAddrLen* se omiten para los sockets de SOCK_STREAM.

Para los sockets de datagramas, los datos se extraen del primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con `ReceiveFromEx` la primera parte del mensaje, se pierde el exceso de datos y devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE.

Si *lpSockAddr* es distinto de cero y el socket es de tipo SOCK_DGRAM, la dirección de red del socket que envió los datos se copia en la estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) correspondiente. El valor señalado por *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modifica al devolver para indicar el tamaño real de la dirección almacenada allí. Si no hay datos entrantes `ReceiveFromEx` disponibles en el socket, la llamada espera a que lleguen los datos a menos que el socket no se bloquee. En este caso, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. La `OnReceive` devolución de llamada se puede utilizar para determinar cuándo llegan más datos.

Si el socket es de tipo SOCK_STREAM y el lado `ReceiveFromEx` remoto ha apagado la conexión correctamente, un se completará inmediatamente con 0 bytes recibidos.

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Enviar

Llame a esta función miembro para enviar datos en un socket conectado.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un búfer que contiene los datos que se van a transmitir.

*nBufLen*<br/>
La longitud de los datos en *lpBuf* en bytes.

*nFlags*<br/>
Especifica la forma en que se realiza la llamada. La semántica de esta función viene determinada por las opciones de socket y el parámetro *nFlags.* Este último se construye combinando cualquiera de los siguientes valores con el operador **C++ OR:**

- MSG_DONTROUTE Especifica que los datos no deben estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB Enviar datos fuera de banda (solo SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Si no se `Send` produce ningún error, devuelve el número total de caracteres enviados. (Tenga en cuenta que esto puede ser menor que el número indicado por *nBufLen*.) De lo contrario, se devuelve un valor de SOCKET_ERROR y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEACCES La dirección solicitada es una dirección de difusión, pero no se ha establecido el indicador adecuado.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEFAULT El argumento *lpBuf* no está en una parte válida del espacio de direcciones de usuario.

- WSAENETRESET La conexión debe restablecerse porque la implementación de Windows Sockets la ha quitado.

- WSAENOBUFS La implementación de Windows Sockets notifica un interbloqueo de búfer.

- WSAENOTCONN El socket no está conectado.

- WSAENOTSOCK El descriptor no es un socket.

- Se especificó MSG_OOB WSAEOPNOTSUPP, pero el socket no es de tipo SOCK_STREAM.

- WSAESHUTDOWN El socket se ha apagado; no es posible `Send` llamar a `ShutDown` un socket después de que se ha invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK El socket se marca como no bloqueante y la operación solicitada se bloquearía.

- WSAEMSGSIZE El socket es de tipo SOCK_DGRAM y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.

- WSAEINVAL El socket no `Bind`se ha enlazado con .

- WSAECONNABORTED El circuito virtual se anuló debido al tiempo de espera u otro error.

- WSAECONNRESET El circuito virtual fue restablecido por el lado remoto.

### <a name="remarks"></a>Observaciones

`Send`se utiliza para escribir datos salientes en sockets de flujo o datagramas conectados. Para los sockets de datagramas, se debe tener cuidado de no exceder el `iMaxUdpDg` tamaño máximo del paquete IP `AfxSocketInit`de las subredes subyacentes, que es dado por el elemento en la estructura [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) devuelta por . Si los datos son demasiado largos para pasar atómicamente a través del protocolo `GetLastError`subyacente, el error WSAEMSGSIZE se devuelve a través de , y no se transmite ningún dato.

Tenga en cuenta que para un `Send` socket de datagrama la finalización correcta de un no indica que los datos se entregaron correctamente.

En `CAsyncSocket` los objetos de tipo SOCK_STREAM, el número de bytes escritos puede estar entre 1 y la longitud solicitada, dependiendo de la disponibilidad del búfer en los hosts locales y extranjeros.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket::OnSend](#onsend).

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket::SendTo

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
Un búfer que contiene los datos que se van a transmitir.

*nBufLen*<br/>
La longitud de los datos en *lpBuf* en bytes.

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo como "ftp.microsoft.com" o un número punteado como "128.56.22.8".

*nFlags*<br/>
Especifica la forma en que se realiza la llamada. La semántica de esta función viene determinada por las opciones de socket y el parámetro *nFlags.* Este último se construye combinando cualquiera de los siguientes valores con el operador **C++ OR:**

- MSG_DONTROUTE Especifica que los datos no deben estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB Enviar datos fuera de banda (solo SOCK_STREAM).

*lpSockAddr*<br/>
Puntero a una estructura [SOCKADDR](/windows/win32/winsock/sockaddr-2) que contiene la dirección del socket de destino.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Si no se `SendTo` produce ningún error, devuelve el número total de caracteres enviados. (Tenga en cuenta que esto puede ser menor que el número indicado por *nBufLen*.) De lo contrario, se devuelve un valor de SOCKET_ERROR y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEACCES La dirección solicitada es una dirección de difusión, pero no se ha establecido el indicador adecuado.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEFAULT Los parámetros *lpBuf* o *lpSockAddr* no forman parte del espacio de direcciones de usuario o el argumento *lpSockAddr* es demasiado pequeño (menos que el tamaño de una estructura [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL El nombre de host no es válido.

- WSAENETRESET La conexión debe restablecerse porque la implementación de Windows Sockets la ha quitado.

- WSAENOBUFS La implementación de Windows Sockets notifica un interbloqueo de búfer.

- WSAENOTCONN El socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK El descriptor no es un socket.

- Se especificó MSG_OOB WSAEOPNOTSUPP, pero el socket no es de tipo SOCK_STREAM.

- WSAESHUTDOWN El socket se ha apagado; no es posible `SendTo` llamar a `ShutDown` un socket después de que se ha invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK El socket se marca como no bloqueante y la operación solicitada se bloquearía.

- WSAEMSGSIZE El socket es de tipo SOCK_DGRAM y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.

- WSAECONNABORTED El circuito virtual se anuló debido al tiempo de espera u otro error.

- WSAECONNRESET El circuito virtual fue restablecido por el lado remoto.

- WSAEADDRNOTAVAIL La dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden utilizar con este socket.

- WSAEDESTADDRREQ Se requiere una dirección de destino.

- WSAENETUNREACH La red no se puede alcanzar desde este host en este momento.

### <a name="remarks"></a>Observaciones

`SendTo`se utiliza en datagramas o sockets de secuencia y se utiliza para escribir datos salientes en un socket. Para los sockets de datagramas, se debe tener cuidado de no exceder el `iMaxUdpDg` tamaño máximo del paquete IP de las subredes subyacentes, que es dado por el elemento en la estructura [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) rellenada por [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos son demasiado largos para pasar atómicamente a través del protocolo subyacente, se devuelve el error WSAEMSGSIZE y no se transmite ningún dato.

Tenga en cuenta que `SendTo` la finalización correcta de a no indica que los datos se entregaron correctamente.

`SendTo`solo se utiliza en un socket de SOCK_DGRAM para enviar un datagrama a un socket específico identificado por el parámetro *lpSockAddr.*

Para enviar una difusión (solo en un SOCK_DGRAM), la dirección del parámetro *lpSockAddr* debe construirse mediante la dirección IP especial INADDR_BROADCAST (definida en el archivo de encabezado de Windows Sockets WINSOCK. H) junto con el número de puerto previsto. O bien, si el parámetro *lpszHostAddress* es NULL, el socket está configurado para la difusión. Por lo general, es desaconsejable que un datagrama de difusión supere el tamaño en el que puede producirse la fragmentación, lo que implica que la parte de datos del datagrama (excluyendo los encabezados) no debe superar los 512 bytes.

Para controlar direcciones IPv6, utilice [CAsyncSocket::SendToEx](#sendtoex).

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToEx

Llame a esta función miembro para enviar datos a un destino específico (controla direcciones IPv6).

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
Un búfer que contiene los datos que se van a transmitir.

*nBufLen*<br/>
La longitud de los datos en *lpBuf* en bytes.

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo como "ftp.microsoft.com" o un número punteado como "128.56.22.8".

*nFlags*<br/>
Especifica la forma en que se realiza la llamada. La semántica de esta función viene determinada por las opciones de socket y el parámetro *nFlags.* Este último se construye combinando cualquiera de los siguientes valores con el operador **C++ OR:**

- MSG_DONTROUTE Especifica que los datos no deben estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB Enviar datos fuera de banda (solo SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Si no se `SendToEx` produce ningún error, devuelve el número total de caracteres enviados. (Tenga en cuenta que esto puede ser menor que el número indicado por *nBufLen*.) De lo contrario, se devuelve un valor de SOCKET_ERROR y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEACCES La dirección solicitada es una dirección de difusión, pero no se ha establecido el indicador adecuado.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEFAULT Los parámetros *lpBuf* o *lpSockAddr* no forman parte del espacio de direcciones de usuario o el argumento *lpSockAddr* es demasiado pequeño (menos que el tamaño de una estructura [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL El nombre de host no es válido.

- WSAENETRESET La conexión debe restablecerse porque la implementación de Windows Sockets la ha quitado.

- WSAENOBUFS La implementación de Windows Sockets notifica un interbloqueo de búfer.

- WSAENOTCONN El socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK El descriptor no es un socket.

- Se especificó MSG_OOB WSAEOPNOTSUPP, pero el socket no es de tipo SOCK_STREAM.

- WSAESHUTDOWN El socket se ha apagado; no es posible `SendToEx` llamar a `ShutDown` un socket después de que se ha invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK El socket se marca como no bloqueante y la operación solicitada se bloquearía.

- WSAEMSGSIZE El socket es de tipo SOCK_DGRAM y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.

- WSAECONNABORTED El circuito virtual se anuló debido al tiempo de espera u otro error.

- WSAECONNRESET El circuito virtual fue restablecido por el lado remoto.

- WSAEADDRNOTAVAIL La dirección especificada no está disponible en el equipo local.

- Las direcciones WSAEAFNOSUPPORT de la familia especificada no se pueden utilizar con este socket.

- WSAEDESTADDRREQ Se requiere una dirección de destino.

- WSAENETUNREACH La red no se puede alcanzar desde este host en este momento.

### <a name="remarks"></a>Observaciones

Este método es el mismo que [CAsyncSocket::SendTo](#sendto) excepto que controla direcciones IPv6, así como protocolos más antiguos.

`SendToEx`se utiliza en datagramas o sockets de secuencia y se utiliza para escribir datos salientes en un socket. Para los sockets de datagramas, se debe tener cuidado de no exceder el `iMaxUdpDg` tamaño máximo del paquete IP de las subredes subyacentes, que es dado por el elemento en la estructura [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) rellenada por [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos son demasiado largos para pasar atómicamente a través del protocolo subyacente, se devuelve el error WSAEMSGSIZE y no se transmite ningún dato.

Tenga en cuenta que `SendToEx` la finalización correcta de a no indica que los datos se entregaron correctamente.

`SendToEx`solo se utiliza en un socket de SOCK_DGRAM para enviar un datagrama a un socket específico identificado por el parámetro *lpSockAddr.*

Para enviar una difusión (solo en un SOCK_DGRAM), la dirección del parámetro *lpSockAddr* debe construirse mediante la dirección IP especial INADDR_BROADCAST (definida en el archivo de encabezado de Windows Sockets WINSOCK. H) junto con el número de puerto previsto. O bien, si el parámetro *lpszHostAddress* es NULL, el socket está configurado para la difusión. Por lo general, es desaconsejable que un datagrama de difusión supere el tamaño en el que puede producirse la fragmentación, lo que implica que la parte de datos del datagrama (excluyendo los encabezados) no debe superar los 512 bytes.

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockOpt

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
La opción de socket para la que se va a establecer el valor.

*lpOptionValue*<br/>
Puntero al búfer en el que se proporciona el valor de la opción solicitada.

*nOptionLen*<br/>
El tamaño del búfer *lpOptionValue* en bytes.

*nNivel*<br/>
El nivel en el que se define la opción; los únicos niveles admitidos son SOL_SOCKET y IPPROTO_TCP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEFAULT *lpOptionValue* no está en una parte válida del espacio de direcciones de proceso.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAEINVAL *nLevel* no es válido o la información de *lpOptionValue* no es válida.

- WSAENETRESET La conexión ha transcurrido el tiempo de espera cuando se establece SO_KEEPALIVE.

- WSAENOPROTOOPT La opción es desconocida o no es compatible. En particular, SO_BROADCAST no se admite en sockets de tipo SOCK_STREAM, mientras que SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER y SO_OOBINLINE no se admiten en sockets de tipo SOCK_DGRAM.

- La conexión WSAENOTCONN se ha restablecido cuando se fija SO_KEEPALIVE.

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

`SetSockOpt`establece el valor actual de una opción de socket asociada a un socket de cualquier tipo, en cualquier estado. Aunque las opciones pueden existir en varios niveles de protocolo, esta especificación solo define las opciones que existen en el nivel "socket" superior. Las opciones afectan a las operaciones de socket, como si se reciben datos acelerados en el flujo de datos normal, si se pueden enviar mensajes de difusión en el socket, etc.

Hay dos tipos de opciones de socket: opciones booleanas que habilitan o deshabilitan una característica o comportamiento, y opciones que requieren un valor o estructura entero. Para habilitar una opción booleana, *lpOptionValue* apunta a un entero distinto de cero. Para deshabilitar la opción *lpOptionValue* apunta a un entero igual a cero. *nOptionLen* debe ser `sizeof(BOOL)` igual a para las opciones booleanas. Para otras opciones, *lpOptionValue* apunta al entero o estructura que contiene el valor deseado para la opción y *nOptionLen* es la longitud del entero o estructura.

SO_LINGER controla la acción realizada cuando los datos `Close` no enviados se ponen en cola en un socket y se llama a la función para cerrar el socket.

De forma predeterminada, un socket no se puede enlazar (consulte [Enlazar](#bind)) a una dirección local que ya está en uso. En ocasiones, sin embargo, puede ser conveniente "reutilizar" una dirección de esta manera. Puesto que cada conexión se identifica de forma única por la combinación de direcciones locales y remotas, no hay ningún problema con tener dos sockets enlazados a la misma dirección local siempre y cuando las direcciones remotas sean diferentes.

Para informar a la `Bind` implementación de Windows Sockets que no se debe desautorizado una llamada en un socket porque la dirección deseada `Bind` ya está en uso por otro socket, la aplicación debe establecer la opción de socket SO_REUSEADDR para el socket antes de emitir la llamada. Tenga en cuenta que la opción se `Bind` interpreta sólo en el momento de la llamada: por lo tanto, es innecesario (pero inofensivo) establecer `Bind` la opción en un socket que no se va a enlazar a una dirección existente, y establecer o restablecer la opción después de la llamada no tiene ningún efecto en este o cualquier otro socket.

Una aplicación puede solicitar que la implementación de Windows Sockets habilite el uso de paquetes "keep-alive" en conexiones de Protocolo de control de transmisión (TCP) activando la opción de socket SO_KEEPALIVE. Una implementación de Windows Sockets no necesita admitir el uso de keep-alives: si lo hace, la semántica precisa es específica de la implementación, pero debe ajustarse a la sección 4.2.3.6 de RFC 1122: "Requisitos para hosts de Internet — Capas de comunicación." Si se descarta una conexión como resultado de "keep-alives", el código de error WSAENETRESET se devuelve a las llamadas en curso en el socket y cualquier llamada posterior producirá un error con WSAENOTCONN.

La opción TCP_NODELAY deshabilita el algoritmo Nagle. El algoritmo Nagle se utiliza para reducir el número de paquetes pequeños enviados por un host almacenando en búfer los datos de envío no reconocidos hasta que se pueda enviar un paquete de tamaño completo. Sin embargo, para algunas aplicaciones este algoritmo puede impedir el rendimiento, y TCP_NODELAY se puede utilizar para desactivarlo. Los escritores de aplicaciones no deben establecer TCP_NODELAY a menos que el impacto de hacerlo sea bien entendido y deseado, ya que establecer TCP_NODELAY puede tener un impacto negativo significativo en el rendimiento de la red. TCP_NODELAY es la única opción de socket compatible que utiliza IPPROTO_TCP de nivel; todas las demás opciones utilizan el nivel SOL_SOCKET.

Algunas implementaciones de Windows Sockets proporcionan información de depuración de salida si una aplicación establece la opción SO_DEBUG.

Las siguientes opciones `SetSockOpt`son compatibles con . El type identifica el tipo de datos direccionados por *lpOptionValue*.

|Value|Tipo|Significado|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Permitir la transmisión de mensajes de difusión en el socket.|
|SO_DEBUG|BOOL|Registra información de depuración.|
|SO_DONTLINGER|BOOL|No bloquee `Close` la espera de que se envíen datos no enviados. Establecer esta opción equivale a `l_onoff` establecer SO_LINGER con establecido en cero.|
|SO_DONTROUTE|BOOL|No rutee: envíalo directamente a la interfaz.|
|SO_KEEPALIVE|BOOL|Envía vidas de keep-alives.|
|SO_LINGER|`struct LINGER`|Permanezca `Close` si hay datos no enviados.|
|SO_OOBINLINE|BOOL|Reciba datos fuera de banda en el flujo de datos normal.|
|SO_RCVBUF|**int**|Especifique el tamaño del búfer para las recibir.|
|SO_REUSEADDR|BOOL|Permita que el socket se ate a una dirección que ya está en uso. (Consulte [Enlazar](#bind).)|
|SO_SNDBUF|**int**|Especifique el tamaño del búfer para los envíos.|
|TCP_NODELAY|BOOL|Deshabilita el algoritmo de Nagle para la fusión de envíos.|

Las opciones de Berkeley Software `SetSockOpt` Distribution (BSD) no compatibles son:

|Value|Tipo|Significado|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket está escuchando|
|SO_ERROR|**int**|Obtener el estado del error y borrar.|
|SO_RCVLOWAT|**int**|Reciba una marca de agua baja.|
|SO_RCVTIMEO|**int**|Tiempo de espera de recepción|
|SO_SNDLOWAT|**int**|Envíe una marca de agua baja.|
|SO_SNDTIMEO|**int**|Enviar tiempo de espera.|
|SO_TYPE|**int**|Tipo de zócalo.|
|IP_OPTIONS||Establecer campo de opciones en encabezado IP.|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::ShutDown

Llame a esta función miembro para deshabilitar los envíos, las recibes o ambos en el socket.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parámetros

*Nhow*<br/>
Marca que describe qué tipos de operación ya no se permitirán, utilizando los siguientes valores enumerados:

- **recibe 0**

- **envía a 1**

- **tanto 2**

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y se puede recuperar un código de error específico llamando a [GetLastError](#getlasterror). Los siguientes errores se aplican a esta función miembro:

- WSANOTINITIALISED Debe producirse un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) correcto antes de usar esta API.

- WSAENETDOWN La implementación de Windows Sockets detectó que el subsistema de red ha fallado.

- WSAEINVAL *nCómo* no es válido.

- WSAEINPROGRESS Una operación de bloqueo de Windows Sockets está en curso.

- WSAENOTCONN El socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK El descriptor no es un socket.

### <a name="remarks"></a>Observaciones

`ShutDown`se utiliza en todo tipo de tomas para desactivar la recepción, transmisión o ambos. Si *nHow* es 0, las siguientes recibir en el socket no se permitirán. Esto no tiene ningún efecto en las capas de protocolo inferiores.

Para el Protocolo de control de transmisión (TCP), la ventana TCP no se cambia y los datos entrantes se aceptarán (pero no se reconocerán) hasta que se agote la ventana. Para User Datagram Protocol (UDP), se aceptan y ponen en cola los datagramas entrantes. En ningún caso se generará un paquete de error ICMP. Si *nHow* es 1, los envíos posteriores no se permiten. Para los sockets TCP, se enviará un FIN. Establecer *nCómo se* deshabilita tanto los envíos como los recibes como se ha descrito anteriormente.

Tenga `ShutDown` en cuenta que no cierra el socket y los `Close` recursos conectados al socket no se liberarán hasta que se llame. Una aplicación no debe confiar en poder reutilizar un socket después de que se haya apagado. En particular, una implementación de Windows Sockets `Connect` no es necesaria para admitir el uso de un socket de este tipo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Socket

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

*Levent*<br/>
Una máscara de bits que especifica una combinación de eventos de red en los que la aplicación está interesada.

- `FD_READ`: Desea recibir una notificación de preparación para la lectura.

- `FD_WRITE`: Desea recibir una notificación de preparación para la escritura.

- `FD_OOB`: Desea recibir una notificación de la llegada de datos fuera de banda.

- `FD_ACCEPT`: Desea recibir una notificación de las conexiones entrantes.

- `FD_CONNECT`: Desea recibir una notificación de conexión completada.

- `FD_CLOSE`: Desea recibir una notificación de cierre de zócalo.

*nProtocolType*<br/>
Protocolo que se utilizará con el socket específico de la familia de direcciones indicada.

*nAddressFormat*<br/>
Especificación de la familia de direcciones.

### <a name="return-value"></a>Valor devuelto

Devuelve `TRUE` si la operación se realiza correctamente; de lo contrario, devuelve `FALSE`.

### <a name="remarks"></a>Observaciones

Este método asigna un identificador de socket. No llama a [CAsyncSocket::Bind](#bind) para enlazar el socket a una `Bind` dirección especificada, por lo que debe llamar más adelante para enlazar el socket a una dirección especificada. Puede usar [CAsyncSocket::SetSockOpt](#setsockopt) para establecer la opción de socket antes de que se enlace.

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
