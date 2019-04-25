---
title: CAsyncSocket (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: ef486e653eaf78914ea25663e0c1ab744ab30cd4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164916"
---
# <a name="casyncsocket-class"></a>CAsyncSocket (clase)

Representa un Socket de Windows, un punto de conexión de comunicación de red.

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
|[CAsyncSocket::Accept](#accept)|Acepta una conexión en el socket.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Notificación de eventos de las solicitudes para el socket.|
|[CAsyncSocket::Attach](#attach)|Asocia un identificador de socket a un `CAsyncSocket` objeto.|
|[CAsyncSocket::Bind](#bind)|Asocia una dirección local del socket.|
|[CAsyncSocket::Close](#close)|Cierra el socket.|
|[CAsyncSocket::Connect](#connect)|Establece una conexión a un socket del mismo nivel.|
|[CAsyncSocket::Create](#create)|Crea un socket.|
|[CAsyncSocket::Detach](#detach)|Desasocia un identificador de socket desde un `CAsyncSocket` objeto.|
|[CAsyncSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CAsyncSocket` objeto, dado un identificador de socket.|
|[CAsyncSocket::GetLastError](#getlasterror)|Obtiene el estado de error de la última operación con error.|
|[CAsyncSocket::GetPeerName](#getpeername)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtiene la dirección del socket del mismo nivel al que el socket está conectados (identificadores de las direcciones IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Obtiene el nombre local para un socket.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtiene el nombre local para un socket (controla las direcciones IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Recupera una opción de socket.|
|[CAsyncSocket::IOCtl](#ioctl)|Controla el modo del socket.|
|[CAsyncSocket::Listen](#listen)|Establece un socket para escuchar las solicitudes de conexión entrante.|
|[CAsyncSocket::Receive](#receive)|Recibe los datos desde el socket.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Recibe un datagrama y almacena la dirección de origen.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Recibe un datagrama y almacena la dirección de origen (controla las direcciones IPv6).|
|[CAsyncSocket::Send](#send)|Envía datos a un socket conectado.|
|[CAsyncSocket::SendTo](#sendto)|Envía datos a un destino concreto.|
|[CAsyncSocket::SendToEx](#sendtoex)|Envía datos a un destino concreto (controla las direcciones IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Establece una opción de socket.|
|[CAsyncSocket::ShutDown](#shutdown)|Deshabilita `Send` o `Receive` llama en el socket.|
|[CASyncSocket::Socket](#socket)|Asigna un identificador de socket.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Notifica a un socket de escucha que puede aceptar solicitudes de conexión pendientes llamando `Accept`.|
|[CAsyncSocket::OnClose](#onclose)|Notifica a un socket que el socket conectado a ella ha cerrado.|
|[CAsyncSocket::OnConnect](#onconnect)|Notifica a un socket de conexión que el intento de conexión está completado, si correctamente o no.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Notifica a un socket de recepción que no hay datos fuera de banda para su lectura en el socket, normalmente un mensaje urgente.|
|[CAsyncSocket::OnReceive](#onreceive)|Notifica a un socket de escucha que no hay datos que va a recuperar mediante una llamada a `Receive`.|
|[CAsyncSocket::OnSend](#onsend)|Notifica a un socket que puede enviar datos mediante una llamada a `Send`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|Asigna un nuevo valor a un `CAsyncSocket` objeto.|
|[CAsyncSocket::operator SOCKET](#operator_socket)|Utilice este operador para recuperar el identificador SOCKET de la `CAsyncSocket` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indica el identificador del SOCKET asociado a este `CAsyncSocket` objeto.|

## <a name="remarks"></a>Comentarios

Clase `CAsyncSocket` encapsula la API de las funciones de Socket de Windows, que proporciona una abstracción orientada a objetos para los programadores que deseen utilizar Windows Sockets en conjunción con MFC.

Esta clase se basa en el supuesto de que entiende las comunicaciones de red. Es responsable de controlar el bloqueo de las diferencias de orden de bytes, y las conversiones entre Unicode y juegos de caracteres multibyte establecer las cadenas (MBCS). Si desea que una interfaz más útil que administra estos problemas en su nombre, vea la clase [CSocket](../../mfc/reference/csocket-class.md).

Para usar un `CAsyncSocket` de objeto, llame a su constructor, a continuación, llame a la [crear](#create) función para crear el identificador de socket subyacente (tipo `SOCKET`), excepto en sockets aceptados. Para una llamada de socket de servidor el [escuchar](#listen) función miembro y para una llamada de socket de cliente la [Connect](#connect) función miembro. El socket de servidor debe llamar a la [Accept](#accept) función al recibir una solicitud de conexión. Use los restantes `CAsyncSocket` funciones para llevar a cabo las comunicaciones entre los sockets. Al finalizar, destruir la `CAsyncSocket` si se ha creado en el montón de objeto; el destructor llama automáticamente a la [cerrar](#close) función. El tipo de datos SOCKET se describe en el artículo [Windows Sockets: en segundo plano](../../mfc/windows-sockets-background.md).

> [!NOTE]
>  Cuando se usa sockets MFC en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se llama sólo en el subproceso principal.

Para obtener más información, consulte [Windows Sockets: Usar la clase CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) y artículos relacionados., así como [API de Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsock.h

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
Una referencia que identifica un nuevo socket que está disponible para la conexión.

*lpSockAddr*<br/>
Un puntero a un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que recibe la dirección de la conexión de socket, como conoce en la red. El formato exacto de la *lpSockAddr* argumento viene determinada por la familia de direcciones que se establece cuando se creó el socket. Si *lpSockAddr* o *lpSockAddrLen* son iguales a NULL, se devuelve ninguna información sobre la dirección remota del socket aceptado.

*lpSockAddrLen*<br/>
Un puntero a la longitud de la dirección en *lpSockAddr* en bytes. El *lpSockAddrLen* es un parámetro de resultado del valor: debe contener la cantidad de espacio que señala inicialmente *lpSockAddr*; la longitud real (en bytes) de la dirección devuelta contendrá la devolución.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento es demasiado pequeño (menor que el tamaño de un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura).

- A WSAEINPROGRESS que llamar al bloqueo Sockets de Windows está en curso.

- WSAEINVAL `Listen` no fue invocado antes de Aceptar.

- WSAEMFILE la cola está vacía al entrar para aceptar y no hay ningún descriptores disponibles.

- Espacio en búfer WSAENOBUFS No está disponible.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEOPNOTSUPP el socket que se hace referencia no es un tipo que admita servicios orientados a conexiones.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y no hay conexiones están presentes para que se acepte.

### <a name="remarks"></a>Comentarios

Esta rutina extrae la primera conexión de la cola de conexiones pendientes, crea un nuevo socket con las mismas propiedades que este socket y lo adjunta a *rConnectedSocket*. Si están presentes en la cola, no hay conexiones pendientes `Accept` devuelve cero y `GetLastError` devuelve un error. El socket aceptado ( *rConnectedSocket)* no se puede usar para aceptar más conexiones. El socket original permanece abierto y a la escucha.

El argumento *lpSockAddr* es un parámetro de resultado que se rellena con la dirección del socket de conexión, ya sabe que la capa de comunicaciones. `Accept` se utiliza con tipos de socket basadas en la conexión como SOCK_STREAM.

##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect

Llame a esta función miembro para solicitar la notificación de eventos para un socket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parámetros

*lEvent*<br/>
Máscara de bits que especifica una combinación de los eventos de red en el que está interesada la aplicación.

- FD_READ desea recibir una notificación de preparación para la lectura.

- FD_WRITE desea recibir una notificación cuando los datos están disponibles para su lectura.

- FD_OOB desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT desea recibir una notificación de los resultados de la conexión.

- FD_CLOSE desea recibir una notificación cuando se cerró un socket de un elemento del mismo nivel.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEINVAL indica que uno de los parámetros especificados no era válido.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

### <a name="remarks"></a>Comentarios

Esta función se utiliza para especificar qué funciones de notificación de devolución de llamada MFC se llamará para el socket. `AsyncSelect` establece automáticamente este socket en modo de no bloqueo. Para obtener más información, vea el artículo [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="attach"></a>  CAsyncSocket::Attach

Llame a esta función miembro para adjuntar el *hSocket* identificador de un `CAsyncSocket` objeto.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador a un socket.

*lEvent*<br/>
Máscara de bits que especifica una combinación de los eventos de red en el que está interesada la aplicación.

- FD_READ desea recibir una notificación de preparación para la lectura.

- FD_WRITE desea recibir una notificación cuando los datos están disponibles para su lectura.

- FD_OOB desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT desea recibir una notificación de los resultados de la conexión.

- FD_CLOSE desea recibir una notificación cuando se cerró un socket de un elemento del mismo nivel.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente.

### <a name="remarks"></a>Comentarios

El identificador de SOCKET se almacena en el objeto [m_hSocket](#m_hsocket) miembro de datos.

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

*nSocketPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszSocketAddress*<br/>
La dirección de red, un número separado por puntos, como "128.56.22.8". Pasar el valor NULL de cadena para este parámetro indica el `CAsyncSocket` instancia debe escuchar la actividad del cliente en todas las interfaces de red.

*lpSockAddr*<br/>
Un puntero a un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que contiene la dirección que se asigna a este socket.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEADDRINUSE la dirección especificada ya está en uso. (Vea la opción de socket SO_REUSEADDR bajo [SetSockOpt](#setsockopt).)

- WSAEFAULT el *nSockAddrLen* argumento es demasiado pequeño (menor que el tamaño de un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura).

- A WSAEINPROGRESS que llamar al bloqueo Sockets de Windows está en curso.

- WSAEAFNOSUPPORT la familia de direcciones especificado no es compatible con este puerto.

- WSAEINVAL el socket ya está enlazado a una dirección.

- Almacena en búfer disponible, no WSAENOBUFS suficientemente demasiadas conexiones.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Esta rutina se utiliza en un datagrama no conectado o un socket de secuencia, que antes posteriores `Connect` o `Listen` llamadas. Antes de que puede aceptar las solicitudes de conexión, un socket de servidor escucha debe seleccionar un número de puerto y comunicar a los Sockets de Windows mediante una llamada a `Bind`. `Bind` establece la asociación de local (número de puerto y dirección de host) del socket asignando un nombre local a un socket sin nombre.

##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket

Construye un objeto de socket en blanco.

```
CAsyncSocket();
```

### <a name="remarks"></a>Comentarios

Después de crear el objeto, se debe llamar a su `Create` función miembro para crear la estructura de datos SOCKET y enlazar su dirección. (En el servidor de una comunicación de Windows Sockets, cuando el socket de escucha crea un socket para usar en el `Accept` llamada, no se llama `Create` para ese socket.)

##  <a name="close"></a>  CAsyncSocket::Close

Cierra el socket.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Esta función libera el descriptor de socket para que aún más las referencias a él se producirá el error WSAENOTSOCK. Si se trata de la última referencia al socket subyacente, la información asociada de nomenclatura y los datos en cola se descartan. Llamadas de destructor del objeto de socket `Close` para usted.

Para `CAsyncSocket`, pero no para `CSocket`, la semántica de `Close` se ven afectados por las opciones de socket SO_LINGER y SO_DONTLINGER. Para obtener más información, vea la función miembro `GetSockOpt`.

##  <a name="connect"></a>  CAsyncSocket::Connect

Llame a esta función miembro para establecer una conexión a un socket de datagrama o la secuencia no conectado.

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
La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número separado por puntos, como "128.56.22.8".

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpSockAddr*<br/>
Un puntero a un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que contiene la dirección del socket conectado.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Si indica un código de error de WSAEWOULDBLOCK y la aplicación utiliza las devoluciones de llamada reemplazables, la aplicación recibirá una `OnConnect` mensaje una vez completada la operación de conexión. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEADDRINUSE la dirección especificada ya está en uso.

- A WSAEINPROGRESS que llamar al bloqueo Sockets de Windows está en curso.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- WSAEAFNOSUPPORT direcciones de la familia especificada no se puede usar con este socket.

- WSAECONNREFUSED se rechazó el intento de conexión.

- Se requiere WSAEDESTADDRREQ A dirección de destino.

- WSAEFAULT el *nSockAddrLen* argumento sea incorrecto.

- Dirección de host WSAEINVAL no válido.

- WSAEISCONN el socket ya está conectado.

- N WSAEMFILE más descriptores de archivo están disponibles.

- WSAENETUNREACH la red no se puede alcanzar desde este host en este momento.

- Espacio en búfer WSAENOBUFS No está disponible. No se puede conectar el socket.

- WSAENOTSOCK el descriptor no es un socket.

- WSAETIMEDOUT intento de conexión agotó el tiempo de espera sin establecer una conexión.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y no se puede completar inmediatamente la conexión.

### <a name="remarks"></a>Comentarios

Si el socket no está enlazado, valores únicos se asignan a la asociación local por el sistema y el socket está marcado como dependiente. Observe que si el campo de dirección de la estructura de nombre es todo ceros `Connect` devolverá cero. Para obtener información de error extendida, llame a la `GetLastError` función miembro.

Para los sockets de secuencia (tipo SOCK_STREAM), se inicia una conexión activa al host externo. Cuando la llamada de socket se completa correctamente, el socket está listo para enviar y recibir datos.

Para un socket de datagrama (tipo SOCK_DGRAM), se establece un destino predeterminado, que se usará en posteriores `Send` y `Receive` llamadas.

##  <a name="create"></a>  CAsyncSocket::Create

Llame a la `Create` función miembro después de crear un objeto de socket para crear el socket de Windows y adjuntarlo.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
Un puerto conocido para usarse con el socket, o 0 si desea que Windows Sockets para seleccionar un puerto.

*nSocketType*<br/>
SOCK_STREAM o SOCK_DGRAM.

*lEvent*<br/>
Máscara de bits que especifica una combinación de los eventos de red en el que está interesada la aplicación.

- FD_READ desea recibir una notificación de preparación para la lectura.

- FD_WRITE desea recibir una notificación de preparación para escribir en él.

- FD_OOB desea recibir una notificación de la llegada de datos fuera de banda.

- FD_ACCEPT desea recibir una notificación de las conexiones entrantes.

- FD_CONNECT desea recibir una notificación de conexión completa.

- FD_CLOSE desea recibir una notificación de cierre del socket.

*lpszSockAddress*<br/>
Un puntero a una cadena que contiene la dirección de red del socket conectado, un número separado por puntos, como "128.56.22.8". Pasar el valor NULL de cadena para este parámetro indica el `CAsyncSocket` instancia debe escuchar la actividad del cliente en todas las interfaces de red.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- No se admite WSAEAFNOSUPPORT la familia de direcciones especificado.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- N WSAEMFILE más descriptores de archivo están disponibles.

- Espacio en búfer WSAENOBUFS No está disponible. No se puede crear el socket.

- No se admite WSAEPROTONOSUPPORT el puerto especificado.

- WSAEPROTOTYPE el puerto especificado es del tipo incorrecto para este socket.

- WSAESOCKTNOSUPPORT el tipo de socket especificado no se admite en esta familia de direcciones.

### <a name="remarks"></a>Comentarios

`Create` las llamadas [Socket](#socket) y si se realiza correctamente, llama a [enlazar](#bind) para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:

- SOCK_STREAM proporciona secuenciado, secuencias de bytes confiable, dúplex completo y basada en la conexión. Usa el protocolo de Control de transmisión (TCP) para la familia de direcciones de Internet.

- SOCK_DGRAM admite datagramas, que son paquetes sin conexión no confiables de longitud máxima fija (normalmente corta). Usa el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet.

    > [!NOTE]
    >  El `Accept` función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. No llame a `Create` para este nuevo objeto de socket.

> [!IMPORTANT]
> `Create` es **no** segura para subprocesos.  Si se llama en un entorno multiproceso donde podría invocarse simultáneamente mediante subprocesos diferentes, asegúrese de proteger cada llamada con una exclusión mutua u otro bloqueo de sincronización.

Para obtener más información acerca de los sockets de datagrama y de secuencia, consulte los artículos [Windows Sockets: En segundo plano](../../mfc/windows-sockets-background.md) y [Windows Sockets: Puertos y direcciones de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md) y [API de Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>  CAsyncSocket::Detach

Llame a esta función miembro para desconectar el identificador SOCKET en el *m_hSocket* miembro de datos desde el `CAsyncSocket` de objeto y establecer *m_hSocket* en NULL.

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
Contiene un identificador a un socket.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CAsyncSocket` de objeto, o NULL si no existe ningún `CAsyncSocket` objeto asociado al *hSocket*.

### <a name="remarks"></a>Comentarios

Cuando se especifica un identificador de SOCKET, si un `CAsyncSocket` objeto no está asociado al identificador, la función miembro devuelve NULL.

##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError

Llame a esta función miembro para obtener el estado de error de la última operación con error.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto indica el código de error para la rutina de Windows Sockets API último realizada por este subproceso.

### <a name="remarks"></a>Comentarios

Cuando una función miembro determinada indica que se produjo un error, `GetLastError` debe llamarse para recuperar el código de error adecuado. Vea las descripciones de la función miembro individual para obtener una lista de códigos de error aplicable.

Para obtener más información acerca de los códigos de error, consulte [API de Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

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
Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.

*rPeerPort*<br/>
Referencia a un tipo UINT que almacena un puerto.

*lpSockAddr*<br/>
Un puntero a la [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que recibe el nombre del socket del mismo nivel.

*lpSockAddrLen*<br/>
Un puntero a la longitud de la dirección en *lpSockAddr* en bytes. Si la devolución, el *lpSockAddrLen* argumento contiene el tamaño real de *lpSockAddr* devuelto en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento no es lo suficientemente grande.

- A WSAEINPROGRESS que llamar al bloqueo Sockets de Windows está en curso.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Para controlar las direcciones IPv6, use [CAsyncSocket::GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx

Llame a esta función miembro para obtener la dirección del socket del mismo nivel al que este socket está conectados (identificadores de las direcciones IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parámetros

*rPeerAddress*<br/>
Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.

*rPeerPort*<br/>
Referencia a un tipo UINT que almacena un puerto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento no es lo suficientemente grande.

- A WSAEINPROGRESS que llamar al bloqueo Sockets de Windows está en curso.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Esta función es el mismo que [CAsyncSocket::GetPeerName](#getpeername) , salvo que lo administre IPv6 anteriores, así como protocolos de direcciones.

##  <a name="getsockname"></a>  CAsyncSocket::GetSockName

Llame a esta función miembro para obtener el nombre local para un socket.

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
Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.

*rSocketPort*<br/>
Referencia a un tipo UINT que almacena un puerto.

*lpSockAddr*<br/>
Un puntero a un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que recibe la dirección del socket.

*lpSockAddrLen*<br/>
Un puntero a la longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento no es lo suficientemente grande.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEINVAL el socket no está enlazado a una dirección con `Bind`.

### <a name="remarks"></a>Comentarios

Esta llamada es especialmente útil cuando un `Connect` se ha realizado la llamada sin realizar una `Bind` primero; esta llamada proporciona el único medio por el que puede determinar la asociación local que se ha establecido por el sistema.

Para controlar las direcciones IPv6, use [CAsyncSocket::GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx

Llame a esta función miembro para obtener el nombre local para un socket (controla las direcciones IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parámetros

*rSocketAddress*<br/>
Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.

*rSocketPort*<br/>
Referencia a un tipo UINT que almacena un puerto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento no es lo suficientemente grande.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEINVAL el socket no está enlazado a una dirección con `Bind`.

### <a name="remarks"></a>Comentarios

Esta llamada es el mismo que [CAsyncSocket::GetSockName](#getsockname) , salvo que lo administre IPv6 anteriores, así como protocolos de direcciones.

Esta llamada es especialmente útil cuando un `Connect` se ha realizado la llamada sin realizar una `Bind` primero; esta llamada proporciona el único medio por el que puede determinar la asociación local que se ha establecido por el sistema.

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
La opción de socket para el que el valor es va a recuperar.

*lpOptionValue*<br/>
Un puntero al búfer en el que el valor de la opción solicitada es va a devolver. Se devuelve el valor asociado con la opción seleccionada en el búfer *lpOptionValue*. El entero apunta *lpOptionLen* originalmente debe contener el tamaño de este búfer en bytes; y la devolución, se establecerá en el tamaño del valor devuelto. Para SO_LINGER, será el tamaño de un `LINGER` estructura; para todas las demás opciones será el tamaño de un valor booleano o un **int**, según la opción. Ver la lista de opciones y sus tamaños en la sección Comentarios.

*lpOptionLen*<br/>
Un puntero al tamaño de la *lpOptionValue* búfer en bytes.

*nLevel*<br/>
El nivel en el que se define la opción; los niveles admitidos solo son SOL_SOCKET y IPPROTO_TCP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Si nunca se ha establecido una opción con `SetSockOpt`, a continuación, `GetSockOpt` devuelve el valor predeterminado para la opción. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpOptionLen* argumento no era válido.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- La opción WSAENOPROTOOPT es desconocido o no compatible. En concreto, SO_BROADCAST no se admite en sockets de tipo SOCK_STREAM mientras SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER y SO_OOBINLINE no se admiten en sockets de tipo SOCK_DGRAM.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

`GetSockOpt` Recupera el valor actual de una opción de socket asociado con un socket de cualquier tipo, en cualquier estado y almacena el resultado en *lpOptionValue*. Las opciones afectan a las operaciones de socket, como el enrutamiento de paquetes, transferencia de datos fuera de banda y así sucesivamente.

Se admiten las siguientes opciones para `GetSockOpt`. El tipo identifica el tipo de datos dirigidos por *lpOptionValue*. La opción TCP_NODELAY usa IPPROTO_TCP nivel; todas las demás opciones utilizan nivel SOL_SOCKET.

|Valor|Tipo|Significado|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket está realizando escuchas.|
|SO_BROADCAST|BOOL|Socket está configurado para la transmisión de mensajes de difusión.|
|SO_DEBUG|BOOL|Está habilitada la depuración.|
|SO_DONTLINGER|BOOL|Si es true, se deshabilita la opción SO_LINGER.|
|SO_DONTROUTE|BOOL|El enrutamiento está deshabilitado.|
|SO_ERROR|**int**|Recuperar el estado de error y borrar.|
|SO_KEEPALIVE|BOOL|Se están enviando abiertas.|
|SO_LINGER|`struct LINGER`|Devuelve las opciones actuales de permanencia.|
|SO_OOBINLINE|BOOL|Está recibiendo datos fuera de banda en el flujo de datos normal.|
|SO_RCVBUF|int|Recibe el tamaño del búfer.|
|SO_REUSEADDR|BOOL|El socket se puede enlazar a una dirección que ya está en uso.|
|SO_SNDBUF|**int**|Tamaño del búfer de envía.|
|SO_TYPE|**int**|El tipo de socket (por ejemplo, SOCK_STREAM).|
|TCP_NODELAY|BOOL|Deshabilita el algoritmo de Nagle para la fusión de envíos.|

Opciones de distribución de Software de Berkeley (BSD) no se admite para `GetSockOpt` son:

|Valor|Tipo|Significado|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Recibir la marca de agua.|
|SO_RCVTIMEO|**int**|Tiempo de espera de recepción.|
|SO_SNDLOWAT|**int**|Enviar la marca de agua.|
|SO_SNDTIMEO|**int**|Tiempo de espera de envío.|
|IP_OPTIONS||Obtener opciones de encabezado IP.|
|TCP_MAXSEG|**int**|Obtiene el tamaño máximo de segmento TCP.|

Una llamada a `GetSockOpt` con una opción dará como resultado un código de error de WSAENOPROTOOPT que se devuelven desde `GetLastError`.

##  <a name="ioctl"></a>  CAsyncSocket::IOCtl

Llame a esta función miembro para controlar el modo de un socket.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parámetros

*lCommand*<br/>
El comando que se ejecuta en el socket.

*lpArgument*<br/>
Un puntero a un parámetro para *lCommand*.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEINVAL *lCommand* no es un comando válido, o *lpArgument* no es un parámetro aceptable para *lCommand*, o el comando no es aplicable al tipo de socket proporcionado .

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

Esta rutina se puede usar en ningún socket en cualquier estado. Sirve para obtener o recuperar parámetros operativos asociados al socket, independiente del subsistema de comunicaciones y protocolo. Se admiten los siguientes comandos:

- FIONBIO de habilitar o deshabilitar el modo sin bloqueo en el socket. El *lpArgument* parámetro apunta a un `DWORD`, que es distinto de cero si es el modo de no bloqueo esté habilitado y cero si tiene que estar deshabilitado. Si `AsyncSelect` se ha emitido en un socket, a continuación, se intenta utilizar `IOCtl` para establecer el socket volver al modo de bloqueo se producirá un error con WSAEINVAL. Para establecer el socket volver al modo de bloqueo y evitar el error WSAEINVAL, primero debe deshabilitar una aplicación `AsyncSelect` mediante una llamada a `AsyncSelect` con el *lEvent* parámetro igual a 0, a continuación, llamar a `IOCtl`.

- FIONREAD de determinar el número máximo de bytes que se pueden leer con una `Receive` llamar desde este socket. El *lpArgument* parámetro apunta a un `DWORD` en el que `IOCtl` almacena el resultado. Si este socket es de tipo SOCK_STREAM, FIONREAD devuelve la cantidad total de datos que pueden leerse en una sola `Receive`; esto es normalmente el mismo que la cantidad total de datos en cola en el socket. Si este socket es de tipo SOCK_DGRAM, FIONREAD devuelve que el tamaño del primer datagrama en cola en el socket.

- SIOCATMARK determinar si se han leído todos los datos de fuera de banda. Esto se aplica solo a un socket de tipo SOCK_STREAM que se ha configurado para la recepción en la línea de datos fuera de banda (SO_OOBINLINE). Si no hay datos fuera de banda está esperando a leer, la operación devuelve distinto de cero. De lo contrario devuelve 0 y la siguiente `Receive` o `ReceiveFrom` realizadas en el socket recuperará algunos o todos los datos anterior a la "marca"; la aplicación debe utilizar la operación SIOCATMARK para determinar si los datos permanecen. Si no hay ningún dato normal antes de los datos (fuera de banda) "urgentes", se recibirán en orden. (Tenga en cuenta que un `Receive` o `ReceiveFrom` nunca se combinen los datos de fuera de banda y normales en la misma llamada.) El *lpArgument* parámetro apunta a un `DWORD` en el que `IOCtl` almacena el resultado.

Esta función es un subconjunto de `ioctl()` que se usa en sockets Berkeley. En concreto, no hay ningún comando que es equivalente a FIOASYNC, mientras que SIOCATMARK es el comando solo de nivel de socket que se admite.

##  <a name="listen"></a>  CAsyncSocket::Listen

Llame a esta función miembro para escuchar las solicitudes de conexión entrantes.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parámetros

*nConnectionBacklog*<br/>
La longitud máxima que puede alcanzar la cola de conexiones pendientes. El intervalo válido es de 1 a 5.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- Se ha convertido WSAEADDRINUSE un intento para realizar escuchas en una dirección está en uso.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEINVAL el socket no se ha enlazado con `Bind` o ya está conectado.

- WSAEISCONN el socket ya está conectado.

- N WSAEMFILE más descriptores de archivo están disponibles.

- Espacio en búfer WSAENOBUFS No está disponible.

- WSAENOTSOCK el descriptor no es un socket.

- WSAEOPNOTSUPP el socket que se hace referencia no es de un tipo que admita la `Listen` operación.

### <a name="remarks"></a>Comentarios

Para aceptar conexiones, el socket se crea por primera vez con `Create`, se especifica un trabajo pendiente para las conexiones entrantes con `Listen`, y, a continuación, se aceptan las conexiones con `Accept`. `Listen` se aplica sólo a sockets que admiten las conexiones, es decir, los de tipo SOCK_STREAM. Este socket se coloca en modo "pasivo" donde se confirma y puestos en cola pendientes de aceptación por el proceso de las conexiones entrantes.

Esta función se utiliza normalmente los servidores (o cualquier aplicación que desea que acepte conexiones) que podría tener más de una solicitud de conexión a la vez: si llega una solicitud de conexión con la cola completa, el cliente recibirá un error con una indicación de WSAECONNREFUSED.

`Listen` intenta continuar funcionando conseguirlos cuando no hay ningún puerto disponible (descriptores). Va a aceptar conexiones hasta que la cola está vacía. Si los puertos están disponibles, una llamada posterior a `Listen` o `Accept` va a rellenar la cola al actual o el más reciente "trabajo pendiente," si es posible y reanudar escucha las conexiones entrantes.

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

Contiene el identificador SOCKET para el socket encapsulado por este `CAsyncSocket` objeto.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>  CAsyncSocket::OnAccept

Lo llama el marco de trabajo para notificar a un socket de escucha que puede aceptar solicitudes de conexión pendientes llamando el [Accept](#accept) función miembro.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los siguientes códigos de error se aplica a la `OnAccept` función miembro:

- **0** la función se ha ejecutado correctamente.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onclose"></a>  CAsyncSocket::OnClose

Lo llama el marco de trabajo para notificar este socket que se cierra el socket conectado mediante su proceso.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnClose` función miembro:

- **0** la función se ha ejecutado correctamente.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAECONNRESET se restableció la conexión en el lado remoto.

- WSAECONNABORTED se anuló la conexión debido al tiempo de espera u otro error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onconnect"></a>  CAsyncSocket::OnConnect

Lo llama el marco de trabajo para notificar al conectar el socket que su intento de conexión se ha completado, ya sea correctamente o error.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnConnect` función miembro:

- **0** la función se ha ejecutado correctamente.

- WSAEADDRINUSE la dirección especificada ya está en uso.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- WSAEAFNOSUPPORT direcciones de la familia especificada no se puede usar con este socket.

- Se rechazó con fuerza WSAECONNREFUSED el intento de conexión.

- Se requiere WSAEDESTADDRREQ A dirección de destino.

- WSAEFAULT el *lpSockAddrLen* argumento sea incorrecto.

- WSAEINVAL el socket ya está enlazado a una dirección.

- WSAEISCONN el socket ya está conectado.

- N WSAEMFILE más descriptores de archivo están disponibles.

- WSAENETUNREACH la red no se puede alcanzar desde este host en este momento.

- Espacio en búfer WSAENOBUFS No está disponible. No se puede conectar el socket.

- WSAENOTCONN el socket no está conectado.

- El descriptor WSAENOTSOCK es un archivo, no es un socket.

- El intento de conexión WSAETIMEDOUT agotó el tiempo de espera sin establecer una conexión.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  En [CSocket](../../mfc/reference/csocket-class.md), el `OnConnect` nunca se llama la función de notificación. Para las conexiones, basta con llamar `Connect`, que se devolverá cuando se complete la conexión (éxito o error). Cómo se controlan las notificaciones de conexión es un detalle de implementación de MFC.

Para obtener más información, consulte [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData

Lo llama el marco de trabajo para notificar al socket receptor que el socket remitente tiene datos fuera de banda para enviar.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnOutOfBandData` función miembro:

- **0** la función se ha ejecutado correctamente.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

### <a name="remarks"></a>Comentarios

Datos fuera de banda están un canal lógicamente independiente que está asociado a cada par de sockets conectados del tipo SOCK_STREAM. El canal se utiliza generalmente para enviar datos urgentes.

MFC es compatible con los datos de fuera de banda, pero los usuarios de la clase `CAsyncSocket` no se recomienda utilizarla. La manera más fácil es crear un segundo socket para transferir estos datos. Para obtener más información acerca de los datos fuera de banda, consulte [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onreceive"></a>  CAsyncSocket::OnReceive

Lo llama el marco de trabajo para notificar este socket que hay datos en el búfer que se puede recuperar mediante una llamada a la `Receive` función miembro.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnReceive` función miembro:

- **0** la función se ha ejecutado correctamente.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>  CAsyncSocket::OnSend

Lo llama el marco de trabajo para notificar el socket que ahora puede enviar datos mediante una llamada a la `Send` función miembro.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parámetros

*nErrorCode*<br/>
El error más reciente en un socket. Los códigos de error siguientes se aplican a la `OnSend` función miembro:

- **0** la función se ha ejecutado correctamente.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Windows Sockets: Las notificaciones de socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>  CAsyncSocket::operator =

Asigna un nuevo valor a un `CAsyncSocket` objeto.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Una referencia a una existente `CAsyncSocket` objeto.

### <a name="remarks"></a>Comentarios

Llame a esta función para copiar uno existente `CAsyncSocket` objeto a otro `CAsyncSocket` objeto.

##  <a name="operator_socket"></a>  CAsyncSocket::operator SOCKET

Utilice este operador para recuperar el identificador SOCKET de la `CAsyncSocket` objeto.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador del objeto SOCKET; en caso contrario, es NULL.

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

*lpBuf*<br/>
Un búfer para los datos entrantes.

*nBufLen*<br/>
La longitud de *lpBuf* en bytes.

*nFlags*<br/>
Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:

- MSG_PEEK ojear los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- Datos de proceso MSG_OOB fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si se produce ningún error, `Receive` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAENOTCONN el socket no está conectado.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es de tipo SOCK_STREAM.

- Se cerró el socket WSAESHUTDOWN; no es posible llamar a `Receive` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y la `Receive` operación causaría un bloqueo.

- WSAEMSGSIZE el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.

- WSAEINVAL el socket no se ha enlazado con `Bind`.

- El circuito virtual WSAECONNABORTED se anuló debido al tiempo de espera u otro error.

- Se restableció el circuito virtual WSAECONNRESET en el lado remoto.

### <a name="remarks"></a>Comentarios

Esta función se utiliza para la secuencia conectada o sockets de datagrama y se usa para leer los datos entrantes.

Para los sockets de tipo SOCK_STREAM, se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y no se ha leído datos fuera de banda, se devolverá solo los datos fuera de banda. La aplicación puede utilizar el `IOCtlSIOCATMARK` opción o [OnOutOfBandData](#onoutofbanddata) para determinar si los datos más fuera de banda permanecen a leerse.

Para los sockets de datagrama, los datos se extraen desde el primer datagrama en cola, hasta alcanzar el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del datagrama, se pierde, el exceso de datos y `Receive` devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE. Si no hay datos de entrada están disponibles en el socket, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. El [OnReceive](#onreceive) función de devolución de llamada se puede usar para determinar cuándo llegan a más datos.

Si el socket es de tipo SOCK_STREAM y el lado remoto ha cerrado la conexión correctamente, un `Receive` finalizará inmediatamente con 0 bytes recibidos. Si se ha restablecido la conexión, un `Receive` se producirá el error WSAECONNRESET.

`Receive` debe llamarse una sola vez por cada vez [CAsyncSocket::OnReceive](#onreceive) se llama.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).

##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom

Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en el [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura o en *rSocketAddress*.

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
Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.

*rSocketPort*<br/>
Referencia a un tipo UINT que almacena un puerto.

*lpSockAddr*<br/>
Un puntero a un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que contiene la dirección de origen cuando se devuelve.

*lpSockAddrLen*<br/>
Un puntero a la longitud de la dirección de origen en *lpSockAddr* en bytes.

*nFlags*<br/>
Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:

- MSG_PEEK ojear los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- Datos de proceso MSG_OOB fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si se produce ningún error, `ReceiveFrom` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar mediante una llamada a `GetLastError`. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento no era válido: el *lpSockAddr* búfer es demasiado pequeño para dar cabida a la dirección del mismo nivel.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEINVAL el socket no se ha enlazado con `Bind`.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es de tipo SOCK_STREAM.

- Se cerró el socket WSAESHUTDOWN; no es posible llamar a `ReceiveFrom` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y la `ReceiveFrom` operación causaría un bloqueo.

- WSAEMSGSIZE el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.

- El circuito virtual WSAECONNABORTED se anuló debido al tiempo de espera u otro error.

- Se restableció el circuito virtual WSAECONNRESET en el lado remoto.

### <a name="remarks"></a>Comentarios

Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se envían los datos.

Para controlar las direcciones IPv6, use [CAsyncSocket::ReceiveFromEx](#receivefromex).

Para los sockets de tipo SOCK_STREAM, se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y no se ha leído datos fuera de banda, se devolverá solo los datos fuera de banda. La aplicación puede utilizar el `IOCtlSIOCATMARK` opción o `OnOutOfBandData` para determinar si los datos más fuera de banda permanecen a leerse. El *lpSockAddr* y *lpSockAddrLen* se omiten los parámetros para los sockets SOCK_STREAM.

Para los sockets de datagrama, los datos se extraen desde el primer datagrama en cola, hasta alcanzar el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del mensaje, se pierde, el exceso de datos y `ReceiveFrom` devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE.

Si *lpSockAddr* es distinto de cero y el socket es de tipo SOCK_DGRAM, la dirección de red del socket que envía los datos se copia en la correspondiente [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura. El valor señalado por *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modificará la devolución para indicar el tamaño real de la dirección que se almacenan allí. Si no hay datos de entrada están disponibles en el socket, el `ReceiveFrom` llamada espera a que lleguen a menos que el socket es datos sin bloqueo. En este caso, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. El `OnReceive` devolución de llamada se puede usar para determinar cuándo llegan a más datos.

Si el socket es de tipo SOCK_STREAM y el lado remoto ha cerrado la conexión correctamente, un `ReceiveFrom` finalizará inmediatamente con 0 bytes recibidos.

##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx

Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en el [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura o en *rSocketAddress* (controla las direcciones IPv6).

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
Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.

*rSocketPort*<br/>
Referencia a un tipo UINT que almacena un puerto.

*nFlags*<br/>
Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:

- MSG_PEEK ojear los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.

- Datos de proceso MSG_OOB fuera de banda.

### <a name="return-value"></a>Valor devuelto

Si se produce ningún error, `ReceiveFromEx` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar mediante una llamada a `GetLastError`. Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT el *lpSockAddrLen* argumento no era válido: el *lpSockAddr* búfer es demasiado pequeño para dar cabida a la dirección del mismo nivel.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEINVAL el socket no se ha enlazado con `Bind`.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es de tipo SOCK_STREAM.

- Se cerró el socket WSAESHUTDOWN; no es posible llamar a `ReceiveFromEx` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 0 o 2.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y la `ReceiveFromEx` operación causaría un bloqueo.

- WSAEMSGSIZE el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.

- El circuito virtual WSAECONNABORTED se anuló debido al tiempo de espera u otro error.

- Se restableció el circuito virtual WSAECONNRESET en el lado remoto.

### <a name="remarks"></a>Comentarios

Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se envían los datos.

Esta función es el mismo que [CAsyncSocket::ReceiveFrom](#receivefrom) , salvo que lo administre IPv6 anteriores, así como protocolos de direcciones.

Para los sockets de tipo SOCK_STREAM, se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket SO_OOBINLINE) y no se ha leído datos fuera de banda, se devolverá solo los datos fuera de banda. La aplicación puede utilizar el `IOCtlSIOCATMARK` opción o `OnOutOfBandData` para determinar si los datos más fuera de banda permanecen a leerse. El *lpSockAddr* y *lpSockAddrLen* se omiten los parámetros para los sockets SOCK_STREAM.

Para los sockets de datagrama, los datos se extraen desde el primer datagrama en cola, hasta alcanzar el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se rellena con la primera parte del mensaje, se pierde, el exceso de datos y `ReceiveFromEx` devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEMSGSIZE.

Si *lpSockAddr* es distinto de cero y el socket es de tipo SOCK_DGRAM, la dirección de red del socket que envía los datos se copia en la correspondiente [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura. El valor señalado por *lpSockAddrLen* se inicializa en el tamaño de esta estructura y se modificará la devolución para indicar el tamaño real de la dirección que se almacenan allí. Si no hay datos de entrada están disponibles en el socket, el `ReceiveFromEx` llamada espera a que lleguen a menos que el socket es datos sin bloqueo. En este caso, se devuelve un valor de SOCKET_ERROR con el código de error establecido en WSAEWOULDBLOCK. El `OnReceive` devolución de llamada se puede usar para determinar cuándo llegan a más datos.

Si el socket es de tipo SOCK_STREAM y el lado remoto ha cerrado la conexión correctamente, un `ReceiveFromEx` finalizará inmediatamente con 0 bytes recibidos.

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
Un búfer que contiene los datos que se transmitan.

*nBufLen*<br/>
La longitud de los datos de *lpBuf* en bytes.

*nFlags*<br/>
Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:

- MSG_DONTROUTE especifica que los datos no deberían estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB enviar datos de fuera de banda (solo SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Si se produce ningún error, `Send` devuelve el número total de caracteres que se envían. (Tenga en cuenta que esto puede ser menor que el número indicado por *nBufLen*.) De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEACCES la dirección solicitada es una dirección de difusión, pero no se estableció el marcador adecuado.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEFAULT el *lpBuf* argumento no es una parte válida del espacio de direcciones del usuario.

- WSAENETRESET la conexión se debe restablecer porque la implementación de Windows Sockets quitó.

- Implementación de WSAENOBUFS The Windows Sockets notifica un interbloqueo de búfer.

- WSAENOTCONN el socket no está conectado.

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es de tipo SOCK_STREAM.

- Se cerró el socket WSAESHUTDOWN; no es posible llamar a `Send` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y se bloqueará la operación solicitada.

- El socket WSAEMSGSIZE es de tipo SOCK_DGRAM y el datagrama es mayor que el límite máximo admitido por la implementación de Windows Sockets.

- WSAEINVAL el socket no se ha enlazado con `Bind`.

- El circuito virtual WSAECONNABORTED se anuló debido al tiempo de espera u otro error.

- Se restableció el circuito virtual WSAECONNRESET en el lado remoto.

### <a name="remarks"></a>Comentarios

`Send` se utiliza para escribir los datos salientes en la secuencia conectada o sockets de datagramas. Para los sockets de datagrama, debe tener cuidado para no superar el tamaño máximo de paquetes IP de las subredes subyacentes, que viene dado por la `iMaxUdpDg` elemento en el [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) estructura devuelta por `AfxSocketInit`. Si los datos están demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error WSAEMSGSIZE se devuelve a través de `GetLastError`, y se transmite ningún dato.

Tenga en cuenta que para un datagrama socket la finalización correcta de un `Send` no indica que los datos se ha entregado correctamente.

En `CAsyncSocket` los objetos de tipo SOCK_STREAM, el número de bytes escritos puede estar entre 1 y la longitud solicitada, según la disponibilidad de búfer en los hosts locales y externas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAsyncSocket::OnSend](#onsend).

##  <a name="sendto"></a>  CAsyncSocket::SendTo

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

*lpBuf*<br/>
Un búfer que contiene los datos que se transmitan.

*nBufLen*<br/>
La longitud de los datos de *lpBuf* en bytes.

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número separado por puntos, como "128.56.22.8".

*nFlags*<br/>
Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:

- MSG_DONTROUTE especifica que los datos no deberían estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB enviar datos de fuera de banda (solo SOCK_STREAM).

*lpSockAddr*<br/>
Un puntero a un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura que contiene la dirección del socket de destino.

*nSockAddrLen*<br/>
La longitud de la dirección en *lpSockAddr* en bytes.

### <a name="return-value"></a>Valor devuelto

Si se produce ningún error, `SendTo` devuelve el número total de caracteres que se envían. (Tenga en cuenta que esto puede ser menor que el número indicado por *nBufLen*.) De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEACCES la dirección solicitada es una dirección de difusión, pero no se estableció el marcador adecuado.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEFAULT el *lpBuf* o *lpSockAddr* parámetros no forman parte del espacio de direcciones del usuario, o la *lpSockAddr* argumento es demasiado pequeño (menor que el tamaño de un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura).

- WSAEINVAL el nombre de host no es válido.

- WSAENETRESET la conexión se debe restablecer porque la implementación de Windows Sockets quitó.

- Implementación de WSAENOBUFS The Windows Sockets notifica un interbloqueo de búfer.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es de tipo SOCK_STREAM.

- Se cerró el socket WSAESHUTDOWN; no es posible llamar a `SendTo` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y se bloqueará la operación solicitada.

- El socket WSAEMSGSIZE es de tipo SOCK_DGRAM y el datagrama es mayor que el límite máximo admitido por la implementación de Windows Sockets.

- El circuito virtual WSAECONNABORTED se anuló debido al tiempo de espera u otro error.

- Se restableció el circuito virtual WSAECONNRESET en el lado remoto.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- WSAEAFNOSUPPORT direcciones de la familia especificada no se puede usar con este socket.

- Se requiere WSAEDESTADDRREQ A dirección de destino.

- WSAENETUNREACH la red no se puede alcanzar desde este host en este momento.

### <a name="remarks"></a>Comentarios

`SendTo` se usa en sockets de datagrama o la secuencia y se utiliza para escribir los datos salientes en un socket. Para los sockets de datagrama, debe tener cuidado para no superar el tamaño máximo de paquetes IP de las subredes subyacentes, que viene dado por la `iMaxUdpDg` elemento en el [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) estructura rellenado por [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos están demasiado largos para pasar de forma atómica a través del protocolo subyacente, se devuelve el error WSAEMSGSIZE y se transmite ningún dato.

Tenga en cuenta que la finalización correcta de un `SendTo` no indica que los datos se ha entregado correctamente.

`SendTo` solo se usa en un socket SOCK_DGRAM para enviar un datagrama a un socket específico identificado por el *lpSockAddr* parámetro.

Para enviar una difusión (en un SOCK_DGRAM solo), la dirección en la *lpSockAddr* parámetro debe crearse con la dirección IP especial INADDR_BROADCAST (definido en el archivo de encabezado de Windows Sockets WINSOCK. (H) junto con el número de puerto deseado. O bien, si la *lpszHostAddress* parámetro es NULL, el socket está configurado para la difusión. No es recomendable por lo general para un datagrama difusión supere el tamaño en el que puede producirse fragmentación, lo cual implica que la parte de datos del datagrama (excepto los encabezados) no debe superar los 512 bytes.

Para controlar las direcciones IPv6, use [CAsyncSocket::SendToEx](#sendtoex).

##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx

Llame a esta función miembro para enviar datos a un destino concreto (controla las direcciones IPv6).

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
Un búfer que contiene los datos que se transmitan.

*nBufLen*<br/>
La longitud de los datos de *lpBuf* en bytes.

*nHostPort*<br/>
El puerto que identifica la aplicación de socket.

*lpszHostAddress*<br/>
La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número separado por puntos, como "128.56.22.8".

*nFlags*<br/>
Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y el *nFlags* parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ **o** operador:

- MSG_DONTROUTE especifica que los datos no deberían estar sujetos a enrutamiento. Un proveedor de Windows Sockets puede optar por omitir esta marca.

- MSG_OOB enviar datos de fuera de banda (solo SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Si se produce ningún error, `SendToEx` devuelve el número total de caracteres que se envían. (Tenga en cuenta que esto puede ser menor que el número indicado por *nBufLen*.) De lo contrario, se devuelve un valor de SOCKET_ERROR y un código de error específico se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEACCES la dirección solicitada es una dirección de difusión, pero no se estableció el marcador adecuado.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEFAULT el *lpBuf* o *lpSockAddr* parámetros no forman parte del espacio de direcciones del usuario, o la *lpSockAddr* argumento es demasiado pequeño (menor que el tamaño de un [SOCKADDR](/windows/desktop/winsock/sockaddr-2) estructura).

- WSAEINVAL el nombre de host no es válido.

- WSAENETRESET la conexión se debe restablecer porque la implementación de Windows Sockets quitó.

- Implementación de WSAENOBUFS The Windows Sockets notifica un interbloqueo de búfer.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

- Se especificó WSAEOPNOTSUPP MSG_OOB, pero el socket no es de tipo SOCK_STREAM.

- Se cerró el socket WSAESHUTDOWN; no es posible llamar a `SendToEx` en un socket después `ShutDown` se ha invocado con *nHow* establecido en 1 o 2.

- WSAEWOULDBLOCK el socket se marca como sin bloqueo y se bloqueará la operación solicitada.

- El socket WSAEMSGSIZE es de tipo SOCK_DGRAM y el datagrama es mayor que el límite máximo admitido por la implementación de Windows Sockets.

- El circuito virtual WSAECONNABORTED se anuló debido al tiempo de espera u otro error.

- Se restableció el circuito virtual WSAECONNRESET en el lado remoto.

- WSAEADDRNOTAVAIL la dirección especificada no está disponible en el equipo local.

- WSAEAFNOSUPPORT direcciones de la familia especificada no se puede usar con este socket.

- Se requiere WSAEDESTADDRREQ A dirección de destino.

- WSAENETUNREACH la red no se puede alcanzar desde este host en este momento.

### <a name="remarks"></a>Comentarios

Este método es igual a [:: SendTo](#sendto) , salvo que lo administre IPv6 anteriores, así como protocolos de direcciones.

`SendToEx` se usa en sockets de datagrama o la secuencia y se utiliza para escribir los datos salientes en un socket. Para los sockets de datagrama, debe tener cuidado para no superar el tamaño máximo de paquetes IP de las subredes subyacentes, que viene dado por la `iMaxUdpDg` elemento en el [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) estructura rellenado por [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos están demasiado largos para pasar de forma atómica a través del protocolo subyacente, se devuelve el error WSAEMSGSIZE y se transmite ningún dato.

Tenga en cuenta que la finalización correcta de un `SendToEx` no indica que los datos se ha entregado correctamente.

`SendToEx` solo se usa en un socket SOCK_DGRAM para enviar un datagrama a un socket específico identificado por el *lpSockAddr* parámetro.

Para enviar una difusión (en un SOCK_DGRAM solo), la dirección en la *lpSockAddr* parámetro debe crearse con la dirección IP especial INADDR_BROADCAST (definido en el archivo de encabezado de Windows Sockets WINSOCK. (H) junto con el número de puerto deseado. O bien, si la *lpszHostAddress* parámetro es NULL, el socket está configurado para la difusión. No es recomendable por lo general para un datagrama difusión supere el tamaño en el que puede producirse fragmentación, lo cual implica que la parte de datos del datagrama (excepto los encabezados) no debe superar los 512 bytes.

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
La opción de socket para el que el valor se va a establecerse.

*lpOptionValue*<br/>
Un puntero al búfer en el que se proporciona el valor de la opción solicitada.

*nOptionLen*<br/>
El tamaño de la *lpOptionValue* búfer en bytes.

*nLevel*<br/>
El nivel en el que se define la opción; los niveles admitidos solo son SOL_SOCKET y IPPROTO_TCP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEFAULT *lpOptionValue* no es una parte del espacio de direcciones de proceso válida.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAEINVAL *nLevel* no es válido, o la información de *lpOptionValue* no es válido.

- WSAENETRESET conexión ha agotado al establecer SO_KEEPALIVE.

- La opción WSAENOPROTOOPT es desconocido o no compatible. En concreto, SO_BROADCAST no se admite en sockets de tipo SOCK_STREAM mientras SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER y SO_OOBINLINE no se admiten en sockets de tipo SOCK_DGRAM.

- Se ha restablecido la conexión WSAENOTCONN cuando se establece SO_KEEPALIVE.

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

`SetSockOpt` establece el valor actual de una opción de socket asociado con un socket de cualquier tipo, en cualquier estado. Aunque las opciones pueden existir en varios niveles de protocolo, esta especificación define solo las opciones que existen en el nivel superior "socket". Las opciones afectan a las operaciones de socket, como si se recepción datos inmediatos en el flujo de datos normales, si en el socket, se pueden enviar mensajes de difusión y así sucesivamente.

Hay dos tipos de opciones de socket: Opciones booleanas que habilitar o deshabilitación una característica o el comportamiento y las opciones que requieren una estructura o un valor entero. Para habilitar una opción booleana, *lpOptionValue* apunta a un entero distinto de cero. Para deshabilitar la opción *lpOptionValue* apunta a un entero igual a cero. *nOptionLen* debe ser igual al `sizeof(BOOL)` para opciones booleanas. Para ver otras opciones, *lpOptionValue* apunta al entero o de estructura que contiene el valor deseado para la opción, y *nOptionLen* es la longitud de la estructura o un entero.

SO_LINGER controla la acción realizada cuando se pone en cola los datos en un socket y el `Close` función se invoca para cerrar el socket.

De forma predeterminada, no se puede enlazar un socket (consulte [enlazar](#bind)) a una dirección local que ya está en uso. En ocasiones, sin embargo, puede ser deseable para una dirección de esta manera "reutilizar". Puesto que todas las conexiones se identifican mediante la combinación de direcciones locales y remotas, no hay ningún problema de tener dos sockets enlazados a la misma dirección local, siempre y cuando las direcciones remotas son diferentes.

Para informar a la implementación de Windows Sockets que un `Bind` llamada en un socket no debe permitirse porque la dirección deseada ya está en uso por otro socket, la aplicación debe establecer la opción de socket SO_REUSEADDR para el socket antes de emitir el `Bind` llamar. Tenga en cuenta que se interpreta la opción solo en el momento de la `Bind` llamar: no, por tanto, es necesario (pero inofensivo) establecer la opción en un socket que no se enlaza a una dirección existente, y establecer o restablecer la opción después de la `Bind` llamada tiene ningún efecto en este u otro socket.

Una aplicación puede solicitar que la implementación de Windows Sockets habilitar el uso de paquetes "keep-alive" en las conexiones de protocolo de Control de transmisión (TCP) al activar la opción de socket SO_KEEPALIVE. Una implementación de Windows Sockets no necesita admitir el uso de abiertas: si es así, la semántica precisa son específicos de la implementación, pero debe ajustarse a la sección 4.2.3.6 de RFC 1122: "Requisitos para Hosts de Internet: niveles de comunicación." Si se quita una conexión como resultado de "abiertas" el código de error WSAENETRESET se devuelve a todas las llamadas en curso en el socket, y las subsiguientes llamadas se producirá un error con WSAENOTCONN.

La opción TCP_NODELAY deshabilita el algoritmo de Nagle. Se utiliza el algoritmo de Nagle para reducir el número de pequeños paquetes enviados por un host mediante el almacenamiento en búfer de envío de los datos hasta que se puede enviar un paquete en tamaño completo. Sin embargo, para algunas aplicaciones de este algoritmo puede perjudicar el rendimiento y TCP_NODELAY puede usarse para desactivarlo. Los escritores de aplicaciones no deben establecer TCP_NODELAY a menos que el impacto de hacerlo es tan deseado y comprendido, ya que establecer TCP_NODELAY puede tener un efecto negativo importante en el rendimiento de red. Es el único tcp_nodelay admite la opción de socket que usa el nivel IPPROTO_TCP; todas las demás opciones utilizan nivel SOL_SOCKET.

Algunas implementaciones de la oferta de Windows Sockets de salida de la información de depuración si se establece la opción SO_DEBUG por una aplicación.

Se admiten las siguientes opciones para `SetSockOpt`. El tipo identifica el tipo de datos dirigidos por *lpOptionValue*.

|Valor|Tipo|Significado|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Permitir la transmisión de mensajes de difusión en el socket.|
|SO_DEBUG|BOOL|Registra información de depuración.|
|SO_DONTLINGER|BOOL|No bloquee `Close` esperando a que se envíen datos no enviados. Al establecer esta opción es equivalente a establecer SO_LINGER con `l_onoff` se establece en cero.|
|SO_DONTROUTE|BOOL|No enrutar: enviar directamente a la interfaz.|
|SO_KEEPALIVE|BOOL|Enviar keepalive.|
|SO_LINGER|`struct LINGER`|Demora `Close` si no enviados los datos están presentes.|
|SO_OOBINLINE|BOOL|Recibir datos fuera de banda en el flujo de datos normal.|
|SO_RCVBUF|**int**|Especificar tamaño del búfer de recibe.|
|SO_REUSEADDR|BOOL|Permitir que el socket se enlace a una dirección que ya está en uso. (Consulte [enlazar](#bind).)|
|SO_SNDBUF|**int**|Especifique el tamaño de búfer para los envíos.|
|TCP_NODELAY|BOOL|Deshabilita el algoritmo de Nagle para la fusión de envíos.|

Opciones de distribución de Software de Berkeley (BSD) no se admite para `SetSockOpt` son:

|Valor|Tipo|Significado|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket está escuchando|
|SO_ERROR|**int**|Obtiene el estado de error y borra.|
|SO_RCVLOWAT|**int**|Recibir la marca de agua.|
|SO_RCVTIMEO|**int**|Tiempo de espera de recepción|
|SO_SNDLOWAT|**int**|Enviar la marca de agua.|
|SO_SNDTIMEO|**int**|Tiempo de espera de envío.|
|SO_TYPE|**int**|Tipo del socket.|
|IP_OPTIONS||Establezca el campo de opciones en el encabezado IP.|

##  <a name="shutdown"></a>  CAsyncSocket::ShutDown

Llamada a esta función miembro para deshabilitar la envía, recibe, o ambos en el socket.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parámetros

*nHow*<br/>
Una marca que describe qué tipos de operación ya no se permitirá, utilizando los valores enumerados siguientes:

- **recibe = 0**

- **envía = 1**

- **both = 2**

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:

- WSANOTINITIALISED A correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de usar esta API.

- Implementación WSAENETDOWN The Windows Sockets había detectado que el subsistema de red.

- WSAEINVAL *nHow* no es válido.

- Operación de Windows Sockets bloqueo WSAEINPROGRESS A está en curso.

- WSAENOTCONN el socket no está conectado (solo SOCK_STREAM).

- WSAENOTSOCK el descriptor no es un socket.

### <a name="remarks"></a>Comentarios

`ShutDown` se utiliza en todos los tipos de sockets para deshabilitar la recepción, transmisión o ambos. Si *nHow* es 0, que recibe subsiguientes en el socket no se permitirá. Esto no tiene ningún efecto en las capas inferiores de protocolo.

Protocolo de Control de transmisión (TCP), no se cambia la ventana TCP y los datos entrantes se aceptan (pero no confirmado) hasta que se agote la ventana. Para el protocolo de datagramas de usuario (UDP), los datagramas entrantes se aceptan y en cola. En ningún caso se generará un paquete de error ICMP. Si *nHow* es 1, no se permiten los envíos posteriores. Para los sockets TCP, se enviará un FIN. Establecer *nHow* a 2 deshabilita tanto los envíos y recepciones como se describió anteriormente.

Tenga en cuenta que `ShutDown` no cierre el socket y los recursos conectados al socket no se liberarán hasta que `Close` se llama. Una aplicación no debe confiar en la capacidad volver a usar un socket una vez que se ha apagado. En concreto, una implementación de Windows Sockets no es necesario para admitir el uso de `Connect` en un socket de este tipo.

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

*nSocketType*<br/>
Especifica `SOCK_STREAM` o `SOCK_DGRAM`.

*lEvent*<br/>
Máscara de bits que especifica una combinación de los eventos de red en el que está interesada la aplicación.

- `FD_READ`: ¿Desea recibir una notificación de preparación para la lectura.

- `FD_WRITE`: ¿Desea recibir una notificación de preparación para escribir en él.

- `FD_OOB`: ¿Desea recibir una notificación de la llegada de datos fuera de banda.

- `FD_ACCEPT`: ¿Desea recibir una notificación de las conexiones entrantes.

- `FD_CONNECT`: ¿Desea recibir una notificación de conexión completa.

- `FD_CLOSE`: ¿Desea recibir una notificación de cierre del socket.

*nProtocolType*<br/>
Protocolo que se usará con el socket que es específico de la familia de direcciones indicado.

*nAddressFormat*<br/>
Especificación para la familia de direcciones.

### <a name="return-value"></a>Valor devuelto

Devuelve `TRUE` si la operación se realiza correctamente; de lo contrario, devuelve `FALSE`.

### <a name="remarks"></a>Comentarios

Este método asigna un identificador de socket. No ejecuta [CAsyncSocket::Bind](#bind) para enlazar el socket a una dirección especificada, por lo que deberá llamar a `Bind` más adelante para enlazar el socket a una dirección especificada. Puede usar [CAsyncSocket::SetSockOpt](#setsockopt) para establecer la opción de socket antes de que está enlazado.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
