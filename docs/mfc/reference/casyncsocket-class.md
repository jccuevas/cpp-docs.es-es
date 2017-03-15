---
title: CAsyncSocket (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAsyncSocket
dev_langs:
- C++
helpviewer_keywords:
- network communications
- asynchronous Windows Sockets
- CAsyncSocket class
- Windows Sockets [C++], asynchronous
- communications [C++], network
- sockets [C++], Windows
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c7a175fc12146d98becc5d06f80e975df5b5a008
ms.lasthandoff: 02/24/2017

---
# <a name="casyncsocket-class"></a>CAsyncSocket (clase)
Representa un Socket de Windows, un extremo de comunicación de red.  
  
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
|[CAsyncSocket:: Accept](#accept)|Acepta una conexión en el socket.|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|Notificación de eventos de solicitudes para el socket.|  
|[CAsyncSocket::Attach](#attach)|Asocia un identificador de socket a un `CAsyncSocket` objeto.|  
|[CAsyncSocket::Bind](#bind)|Asocia una dirección local del socket.|  
|[CAsyncSocket::Close](#close)|Cierra el socket.|  
|[CAsyncSocket:: Connect](#connect)|Establece una conexión a un socket del mismo nivel.|  
|[CAsyncSocket::Create](#create)|Crea un socket.|  
|[CAsyncSocket::Detach](#detach)|Desasocia un identificador de socket desde un `CAsyncSocket` objeto.|  
|[CAsyncSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CAsyncSocket` objeto, dado un identificador de socket.|  
|[CAsyncSocket::GetLastError](#getlasterror)|Obtiene el estado de error de la última operación con error.|  
|[CAsyncSocket::GetPeerName](#getpeername)|Obtiene la dirección del socket del mismo nivel al que está conectado el socket.|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtiene la dirección del socket del mismo nivel al que el socket está conectado (controla direcciones IPv6).|  
|[CAsyncSocket::GetSockName](#getsockname)|Obtiene el nombre local para un socket.|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtiene el nombre local para un socket (controla direcciones IPv6).|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|Recupera una opción de socket.|  
|[CAsyncSocket::IOCtl](#ioctl)|Controla el modo del socket.|  
|[CAsyncSocket:: Listen](#listen)|Establece un socket para escuchar las solicitudes de conexión entrante.|  
|[CAsyncSocket::Receive](#receive)|Recibe los datos desde el socket.|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Recibe un datagrama y almacena la dirección de origen.|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Recibe un datagrama y almacena la dirección de origen (controla direcciones IPv6).|  
|[CAsyncSocket::Send](#send)|Envía datos a un socket conectado.|  
|[:: SendTo](#sendto)|Envía datos a un destino específico.|  
|[CAsyncSocket::SendToEx](#sendtoex)|Envía datos a un destino concreto (controla direcciones IPv6).|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|Establece una opción de socket.|  
|[CAsyncSocket::ShutDown](#shutdown)|Deshabilita **enviar** o **recepción** llama en el socket.|  
|[CASyncSocket::Socket](#socket)|Asigna un identificador de socket.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|Notifica a un socket de escucha puede aceptar solicitudes de conexión pendientes llamando a **Accept**.|  
|[CAsyncSocket::OnClose](#onclose)|Notifica cerró un socket que el socket conectado a él.|  
|[CAsyncSocket::OnConnect](#onconnect)|Notifica a un socket de conexión que el intento de conexión está completo, si correctamente o no.|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Notifica a un socket de recepción que hay datos fuera de banda que leerse en el socket, normalmente un mensaje urgente.|  
|[CAsyncSocket::OnReceive](#onreceive)|Notifica a un socket de escucha que hay datos que desea recuperar mediante una llamada a **recepción**.|  
|[CAsyncSocket::OnSend](#onsend)|Notifica a un socket que se pueden enviar datos al llamar a **enviar**.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|Asigna un nuevo valor a un `CAsyncSocket` objeto.|  
|[CAsyncSocket::operator SOCKET](#operator_socket)|Utilice este operador para recuperar la **SOCKET** identificador de la `CAsyncSocket` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indica el **SOCKET** identificador asociado a esta `CAsyncSocket` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Clase `CAsyncSocket` encapsula la API de Windows Socket para funciones, que proporciona una abstracción orientada a objetos para los programadores que deseen utilizar Windows Sockets en conjunción con MFC.  
  
 Esta clase se basa en el supuesto de que entiende las comunicaciones de red. Usted es responsable de controlar el bloqueo de las diferencias de orden de bytes, y las conversiones entre Unicode y juegos de caracteres multibyte establezca cadenas (MBCS). Si desea que una interfaz más útil que administra estos problemas, vea la clase [CSocket](../../mfc/reference/csocket-class.md).  
  
 Utilizar un `CAsyncSocket` objeto, llame a su constructor, a continuación, llame el [crear](#create) función para crear el identificador de socket subyacente (tipo `SOCKET`), excepto en sockets aceptados. Para una llamada de socket de servidor el [escuchar](#listen) función miembro y para una llamada de socket de cliente la [conectar](#connect) función miembro. El socket de servidor debe llamar a la [Accept](#accept) función al recibir una solicitud de conexión. Utilice los restantes `CAsyncSocket` funciones para llevar a cabo las comunicaciones entre los sockets. Al finalizar, destruir el `CAsyncSocket` si se ha creado en el montón de objeto; el destructor llama automáticamente a la [cerrar](#close) (función). El `SOCKET` tipo de datos se describe en el artículo [Windows Sockets: fondo](../../mfc/windows-sockets-background.md).  
  
> [!NOTE]
>  Al utilizar sockets MFC en subprocesos secundarios en una aplicación MFC vinculado estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se llama sólo en el subproceso principal.  
  
 Para obtener más información, consulte [Windows Sockets: usar clase CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) y artículos relacionados., así como [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsock.h  
  
##  <a name="a-nameaccepta--casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket:: Accept  
 Llame a esta función miembro para aceptar una conexión en un socket.  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `rConnectedSocket`  
 Una referencia identifica un nuevo socket que está disponible para la conexión.  
  
 `lpSockAddr`  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que recibe la dirección de la conexión de socket, como conoce en la red. El formato exacto de la `lpSockAddr` argumento viene determinado por la familia de direcciones establecida cuando se creó el socket. Si `lpSockAddr` o `lpSockAddrLen` son iguales a **NULL**, se devuelve ninguna información sobre la dirección remota del socket aceptado.  
  
 `lpSockAddrLen`  
 Un puntero a la longitud de la dirección en `lpSockAddr` en bytes. El `lpSockAddrLen` es un parámetro de resultado del valor: debe contener la cantidad de espacio que se señala inicialmente `lpSockAddr`; devuelta contendrá la longitud real (en bytes) de la dirección devuelta.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento es demasiado pequeño (menor que el tamaño de una [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINPROGRESS** es una llamada de bloqueo de Windows Sockets en curso.  
  
- **WSAEINVAL** `Listen` no fue invocado antes de Aceptar.  
  
- **WSAEMFILE** la cola está vacía al entrar para aceptar y no hay disponible ningún descriptores.  
  
- `WSAENOBUFS`No hay espacio de búfer está disponible.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP** el socket que se hace referencia no es un tipo que admita el servicio orientado a la conexión.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y no hay conexiones están presentes para ser aceptados.  
  
### <a name="remarks"></a>Comentarios  
 Esta rutina extrae la primera conexión de la cola de conexiones pendientes, crea un nuevo socket con las mismas propiedades que este socket y lo adjunta a `rConnectedSocket`. Si no hay conexiones pendientes en la cola, **Accept** devuelve cero y `GetLastError` devuelve un error. El socket aceptado ( *rConnectedSocket)* no se puede usar para aceptar más conexiones. El socket original permanece abierta y escucha.  
  
 El argumento `lpSockAddr` es un parámetro de resultado que se rellena con la dirección de socket de conexión, tal como conoce el nivel de comunicaciones. **Aceptar** se utiliza con tipos de socket basado en conexión como **SOCK_STREAM**.  
  
##  <a name="a-nameasyncselecta--casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect  
 Llame a esta función miembro para solicitar la notificación de eventos para un socket.  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lEvent`  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- **FD_READ** desea recibir una notificación de preparación para la lectura.  
  
- **FD_WRITE** desea recibir una notificación cuando hay datos disponibles para su lectura.  
  
- **FD_OOB** desea recibir una notificación de la llegada de datos fuera de banda.  
  
- **FD_ACCEPT** desea recibir una notificación de las conexiones entrantes.  
  
- **FD_CONNECT** desea recibir notificación de los resultados de la conexión.  
  
- **FD_CLOSE** desea recibir una notificación cuando se cerró un socket de un elemento del mismo nivel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEINVAL** indica que uno de los parámetros especificados no era válido.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para especificar qué funciones de notificación de devolución de llamada MFC se llamará para el socket. `AsyncSelect`establece automáticamente este socket en modo de no bloqueo. Para obtener más información, vea el artículo [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="a-nameattacha--casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Attach  
 Llame a esta función miembro para adjuntar el `hSocket` identificador de un `CAsyncSocket` objeto.  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hSocket`  
 Contiene un identificador de un socket.  
  
 `lEvent`  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- **FD_READ** desea recibir una notificación de preparación para la lectura.  
  
- **FD_WRITE** desea recibir una notificación cuando hay datos disponibles para su lectura.  
  
- **FD_OOB** desea recibir una notificación de la llegada de datos fuera de banda.  
  
- **FD_ACCEPT** desea recibir una notificación de las conexiones entrantes.  
  
- **FD_CONNECT** desea recibir notificación de los resultados de la conexión.  
  
- **FD_CLOSE** desea recibir una notificación cuando se cerró un socket de un elemento del mismo nivel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 El **SOCKET** identificador se almacena en el objeto [m_hSocket](#m_hsocket) miembro de datos.  
  
##  <a name="a-namebinda--casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Bind  
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
 `nSocketPort`  
 El puerto identifica la aplicación de socket.  
  
 `lpszSocketAddress`  
 La dirección de red, un número de puntos, como "128.56.22.8". Pasar el **NULL** la cadena de este parámetro indica la **CAsyncSocket** instancia debe escuchar la actividad del cliente en todas las interfaces de red.  
  
 `lpSockAddr`  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección que se asigna a este socket.  
  
 `nSockAddrLen`  
 La longitud de la dirección en `lpSockAddr` en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEADDRINUSE** la dirección especificada ya está en uso. (Consulte la **SO_REUSEADDR** opción de socket [SetSockOpt](#setsockopt).)  
  
- **WSAEFAULT** el `nSockAddrLen` argumento es demasiado pequeño (menor que el tamaño de una [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINPROGRESS** es una llamada de bloqueo de Windows Sockets en curso.  
  
- **WSAEAFNOSUPPORT** la familia de direcciones especificado no es compatible con este puerto.  
  
- **WSAEINVAL** el socket ya está enlazado a una dirección.  
  
- `WSAENOBUFS`No hay suficientes búferes disponibles, hay demasiadas conexiones.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Esta rutina se utiliza en un datagrama no conectada o un socket de secuencia, que antes posteriores **conectar** o `Listen` llamadas. Antes de pueda aceptar solicitudes de conexión, un socket de servidor escucha debe seleccionar un número de puerto y ponerlo a conocidos de Windows Sockets mediante una llamada a **enlace**. **Enlazar** establece la asociación local (número de puerto/dirección de host) del socket asignando un nombre local para un socket sin nombre.  
  
##  <a name="a-namecasyncsocketa--casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket  
 Construye un objeto de socket en blanco.  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, se debe llamar a su **crear** función de miembro para crear el **SOCKET** estructura de datos y enlazar su dirección. (En el servidor de una comunicación de Windows Sockets, cuando el socket de escucha crea un socket para usar en el **Accept** llamada, no se llama **crear** para ese socket.)  
  
##  <a name="a-nameclosea--casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Close  
 Cierra el socket.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función libera el descriptor de socket para que aún más las referencias a ella se producirá un error con el error **WSAENOTSOCK**. Si esta es la última referencia al socket subyacente, se descartan la información de nomenclatura asociada y los datos de la cola. Llamadas de destructor del objeto de socket **cerrar** para usted.  
  
 Para `CAsyncSocket`, pero no para `CSocket`, la semántica de **cerrar** se ven afectados por las opciones de socket **SO_LINGER** y **SO_DONTLINGER**. Para obtener más información, vea la función miembro `GetSockOpt`.  
  
##  <a name="a-nameconnecta--casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket:: Connect  
 Llame a esta función miembro para establecer una conexión a un socket de datagrama o la secuencia no conectada.  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszHostAddress`  
 La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número de puntos, como "128.56.22.8".  
  
 `nHostPort`  
 El puerto identifica la aplicación de socket.  
  
 `lpSockAddr`  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección del socket conectado.  
  
 `nSockAddrLen`  
 La longitud de la dirección en `lpSockAddr` en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Si indica un código de error **WSAEWOULDBLOCK**y la aplicación utiliza las devoluciones de llamada reemplazables, su aplicación recibirá una `OnConnect` mensaje una vez completada la operación de conexión. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEADDRINUSE** la dirección especificada ya está en uso.  
  
- **WSAEINPROGRESS** es una llamada de bloqueo de Windows Sockets en curso.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAECONNREFUSED** se rechazó el intento de conexión.  
  
- **WSAEDESTADDRREQ** se requiere una dirección de destino.  
  
- **WSAEFAULT** el `nSockAddrLen` argumento es incorrecto.  
  
- **WSAEINVAL** dirección de host no válido.  
  
- **WSAEISCONN** el socket ya está conectado.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
- `WSAENOBUFS`No hay espacio de búfer está disponible. No se puede conectar el socket.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAETIMEDOUT** intenta conectarse el tiempo de espera sin establecer una conexión.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la conexión no pueden completarse inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 Si el socket no está enlazado, el sistema asigna los valores únicos para la asociación local y el socket se marca como dependiente. Observe que si el campo de dirección de la estructura de nombre es todo ceros **conectar** devolverá cero. Para obtener información de error extendida, llame a la `GetLastError` función miembro.  
  
 Para los sockets de secuencia (tipo **SOCK_STREAM**), se inicia una conexión activa al host externo. Cuando la llamada de socket se completa correctamente, el socket está listo para enviar y recibir datos.  
  
 Para un socket de datagrama (tipo **SOCK_DGRAM**), se establece un destino predeterminado, que se usará en posteriores **enviar** y **recepción** llamadas.  
  
##  <a name="a-namecreatea--casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Create  
 Llame a la **crear** función miembro después de crear un objeto de socket para crear el socket de Windows y adjuntarlo.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSocketPort`  
 Un puerto conocido para usarse con el socket, o 0 si desea que Windows Sockets seleccionar un puerto.  
  
 `nSocketType`  
 **SOCK_STREAM** o **SOCK_DGRAM**.  
  
 `lEvent`  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- **FD_READ** desea recibir una notificación de preparación para la lectura.  
  
- **FD_WRITE** desea recibir una notificación de preparación para la escritura.  
  
- **FD_OOB** desea recibir una notificación de la llegada de datos fuera de banda.  
  
- **FD_ACCEPT** desea recibir una notificación de las conexiones entrantes.  
  
- **FD_CONNECT** desea recibir una notificación de conexión completa.  
  
- **FD_CLOSE** desea recibir una notificación de cierre del socket.  
  
 *lpszSockAddress*  
 Un puntero a una cadena que contiene la dirección de red del socket conectado, un número de puntos, como "128.56.22.8". Pasar el **NULL** la cadena de este parámetro indica la **CAsyncSocket** instancia debe escuchar la actividad del cliente en todas las interfaces de red.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEAFNOSUPPORT** no se admite la familia de direcciones especificado.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- `WSAENOBUFS`No hay espacio de búfer está disponible. No se puede crear el socket.  
  
- **WSAEPROTONOSUPPORT** no se admite el puerto especificado.  
  
- **WSAEPROTOTYPE** el puerto especificado es del tipo incorrecto para este socket.  
  
- **WSAESOCKTNOSUPPORT** no se admite el tipo de socket especificado en esta familia de direcciones.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** llamadas [Socket](#socket) y si se realiza correctamente, llama [enlace](#bind) para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:  
  
- **SOCK_STREAM** proporciona secuenciado, secuencias de bytes confiable, dúplex completo basado en conexión. Utiliza el protocolo de Control de transmisión (TCP) para la familia de direcciones de Internet.  
  
- **SOCK_DGRAM** admite datagramas, que son paquetes sin conexión no confiables de longitud máxima fija (normalmente corta). Utiliza el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet.  
  
    > [!NOTE]
    >  El **Accept** función miembro toma una referencia a un nuevo `CSocket` objeto como su parámetro. Debe construir este objeto antes de llamar a **Accept**. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. No llame a **crear** para este nuevo objeto de socket.  
  
> [!IMPORTANT]
> **Crear** es **no** segura para subprocesos.  Si se llama en un entorno multiproceso que podía invocarse simultáneamente en subprocesos diferentes, asegúrese de proteger cada llamada con una exclusión mutua u otro bloqueo de sincronización.  
  
 Para obtener más información acerca de los sockets de secuencia y datagrama, consulte los artículos [Windows Sockets: fondo](../../mfc/windows-sockets-background.md) y [Windows Sockets: puertos y direcciones de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md) y [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="a-namedetacha--casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach  
 Llame a esta función miembro para separar el **SOCKET** controlar en el `m_hSocket` miembro de datos de la `CAsyncSocket` objeto y establecer `m_hSocket` a **NULL**.  
  
```  
SOCKET Detach();
```  
  
##  <a name="a-namefromhandlea--casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::FromHandle  
 Devuelve un puntero a un `CAsyncSocket` objeto.  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parámetros  
 `hSocket`  
 Contiene un identificador de un socket.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CAsyncSocket` objeto, o **NULL** si no hay ningún `CAsyncSocket` objeto asociado al `hSocket`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se da una **SOCKET** controlar si una `CAsyncSocket` objeto no está asociado al identificador, la función miembro devuelve **NULL**.  
  
##  <a name="a-namegetlasterrora--casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError  
 Llame a esta función miembro para obtener el estado de error de la última operación con error.  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto indica el código de error para la rutina de API de Windows Sockets último realizada por este subproceso.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una función miembro determinada indica que se produjo un error, `GetLastError` se debe llamar para recuperar el código de error adecuado. Consulte las descripciones de la función miembro individual para obtener una lista de códigos de error aplicable.  
  
 Para obtener más información acerca de los códigos de error, consulte [API de Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="a-namegetpeernamea--casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName  
 Llame a esta función miembro para obtener la dirección del socket del mismo nivel al que se conecta este socket.  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parámetros  
 `rPeerAddress`  
 Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.  
  
 `rPeerPort`  
 Hacer referencia a un **UINT** que almacena un puerto.  
  
 `lpSockAddr`  
 Un puntero a la [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que recibe el nombre del socket del mismo nivel.  
  
 `lpSockAddrLen`  
 Un puntero a la longitud de la dirección en `lpSockAddr` en bytes. En la devolución, el `lpSockAddrLen` argumento contiene el tamaño real de `lpSockAddr` devuelto en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento no es suficientemente grande.  
  
- **WSAEINPROGRESS** es una llamada de bloqueo de Windows Sockets en curso.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Para controlar las direcciones IPv6, utilice [CAsyncSocket::GetPeerNameEx](#getpeernameex).  
  
##  <a name="a-namegetpeernameexa--casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx  
 Llame a esta función miembro para obtener la dirección del socket del mismo nivel al que este socket está conectado (controla direcciones IPv6).  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>Parámetros  
 `rPeerAddress`  
 Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.  
  
 `rPeerPort`  
 Hacer referencia a un **UINT** que almacena un puerto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento no es suficientemente grande.  
  
- **WSAEINPROGRESS** es una llamada de bloqueo de Windows Sockets en curso.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es el mismo que [CAsyncSocket::GetPeerName](#getpeername) salvo que controla IPv6 direcciones protocolos así como antiguos.  
  
##  <a name="a-namegetsocknamea--casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName  
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
 `rSocketAddress`  
 Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.  
  
 `rSocketPort`  
 Hacer referencia a un **UINT** que almacena un puerto.  
  
 `lpSockAddr`  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que recibe la dirección del socket.  
  
 `lpSockAddrLen`  
 Un puntero a la longitud de la dirección en `lpSockAddr` en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento no es suficientemente grande.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEINVAL** el socket no se ha enlazado a una dirección con **enlace**.  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada es especialmente útil cuando un **conectar** se ha realizado la llamada sin realizar una **enlace** primero; esta llamada proporciona el único medio por el que puede determinar la asociación local que se ha establecido por el sistema.  
  
 Para controlar las direcciones IPv6, utilice [CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="a-namegetsocknameexa--casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx  
 Llame a esta función miembro para obtener el nombre local de un socket (controla direcciones IPv6).  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSocketAddress`  
 Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.  
  
 `rSocketPort`  
 Hacer referencia a un **UINT** que almacena un puerto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento no es suficientemente grande.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEINVAL** el socket no se ha enlazado a una dirección con **enlace**.  
  
### <a name="remarks"></a>Comentarios  
 Esta llamada es el mismo que [CAsyncSocket::GetSockName](#getsockname) salvo que controla IPv6 direcciones protocolos así como antiguos.  
  
 Esta llamada es especialmente útil cuando un **conectar** se ha realizado la llamada sin realizar una **enlace** primero; esta llamada proporciona el único medio por el que puede determinar la asociación local que se ha establecido por el sistema.  
  
##  <a name="a-namegetsockopta--casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockOpt  
 Llame a esta función miembro para recuperar una opción de socket.  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parámetros  
 `nOptionName`  
 La opción de socket para los que el valor es va a recuperar.  
  
 `lpOptionValue`  
 Un puntero al búfer en el que el valor de la opción solicitada es va a devolver. Se devuelve el valor asociado a la opción seleccionada en el búfer de `lpOptionValue`. El entero que apunta `lpOptionLen` originalmente debe contener el tamaño de este búfer en bytes; y la devolución, se establecerá en el tamaño del valor devuelto. Para **SO_LINGER**, será el tamaño de una `LINGER` estructura; para todas las demás opciones será el tamaño de una **BOOL** o `int`, dependiendo de la opción. Consulte la lista de opciones y sus tamaños en la sección Comentarios.  
  
 `lpOptionLen`  
 Un puntero al tamaño de la `lpOptionValue` búfer en bytes.  
  
 `nLevel`  
 El nivel en el que se define la opción; los niveles admitidos sólo son **SOL_SOCKET** y **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Si nunca se ha establecido una opción con `SetSockOpt`, a continuación, `GetSockOpt` devuelve el valor predeterminado para la opción. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpOptionLen` argumento no era válido.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAENOPROTOOPT** la opción es desconocido o no compatible. En particular, **SO_BROADCAST** no se admite en sockets de tipo **SOCK_STREAM**, mientras que **SO_ACCEPTCONN**, **SO_DONTLINGER**, **SO_KEEPALIVE**, **SO_LINGER**, y **SO_OOBINLINE** no se admite en sockets de tipo **SOCK_DGRAM**.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 `GetSockOpt`Recupera el valor actual de una opción de socket asociado a un socket de cualquier tipo, en cualquier estado y almacena el resultado en `lpOptionValue`. Opciones afectan a las operaciones de socket, como el enrutamiento de paquetes, la transferencia de datos fuera de banda y así sucesivamente.  
  
 Se admiten las siguientes opciones para `GetSockOpt`. El tipo identifica el tipo de datos dirigidos por `lpOptionValue`. El **TCP_NODELAY** opción utiliza nivel **IPPROTO_TCP**; todas las demás opciones utilizan nivel **SOL_SOCKET**.  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Socket está escuchando.|  
|**SO_BROADCAST**|**BOOL**|Socket está configurado para la transmisión de mensajes de difusión.|  
|**SO_DEBUG**|**BOOL**|Está habilitada la depuración.|  
|**SO_DONTLINGER**|**BOOL**|Si es true, el **SO_LINGER** opción está deshabilitada.|  
|**SO_DONTROUTE**|**BOOL**|El enrutamiento está deshabilitado.|  
|**SO_ERROR**|`int`|Recuperar el estado de error y borrar.|  
|**SO_KEEPALIVE**|**BOOL**|Se están enviando abiertas.|  
|**SO_LINGER**|**struct LINGER**|Devuelve las opciones actuales de permanencia.|  
|**SO_OOBINLINE**|**BOOL**|Está recibiendo datos fuera de banda en el flujo normal de datos.|  
|**SO_RCVBUF**|`int`|Recibe el tamaño del búfer.|  
|**SO_REUSEADDR**|**BOOL**|El socket se puede enlazar a una dirección que ya está en uso.|  
|**SO_SNDBUF**|`int`|Envía el tamaño del búfer.|  
|**SO_TYPE**|`int`|El tipo de socket (por ejemplo, **SOCK_STREAM**).|  
|**TCP_NODELAY**|**BOOL**|Deshabilita el algoritmo de Nagle para la fusión de envíos.|  
  
 Opciones de Berkeley Software Distribution (BSD) no se admite para `GetSockOpt` son:  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|`int`|Recibir marca de agua suave.|  
|**SO_RCVTIMEO**|`int`|Tiempo de espera de recepción.|  
|**SO_SNDLOWAT**|`int`|Enviar la marca de agua suave.|  
|**SO_SNDTIMEO**|`int`|Tiempo de espera de envío.|  
|**IP_OPTIONS**||Obtener opciones de encabezado IP.|  
|**TCP_MAXSEG**|`int`|Obtener el tamaño máximo de segmento TCP.|  
  
 Llamar a `GetSockOpt` con una opción no admitida se producirá en el código de error **WSAENOPROTOOPT** que se devuelven desde `GetLastError`.  
  
##  <a name="a-nameioctla--casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl  
 Llame a esta función miembro para controlar el modo de un socket.  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCommand`  
 El comando para llevar a cabo en el socket.  
  
 `lpArgument`  
 Un puntero a un parámetro para `lCommand`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEINVAL** `lCommand` no es un comando válido, o `lpArgument` no es un parámetro aceptable para `lCommand`, o el comando no es aplicable al tipo de socket proporcionado.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 Esta rutina se puede usar en ningún socket en cualquier estado. Se utiliza para obtener o recuperar parámetros operativos asociadas al socket, independiente del subsistema de comunicaciones y protocolo. Se admiten los siguientes comandos:  
  
- **FIONBIO** habilitar o deshabilitar el modo de no bloqueo en el socket. El `lpArgument` parámetro señala a una `DWORD`, que es distinto de cero si se puede habilitar modo de no bloqueo y cero si es que va a deshabilitar. Si `AsyncSelect` se ha emitido en un socket, a continuación, se intenta utilizar **IOCtl** volver a establecer el socket en modo de bloqueo se producirá un error con **WSAEINVAL**. Vuelva a establecer el socket en modo de bloqueo y evitar el **WSAEINVAL** error, primero debe deshabilitar una aplicación `AsyncSelect` llamando a `AsyncSelect` con el `lEvent` parámetro igual a 0, a continuación, llame a **IOCtl**.  
  
- **FIONREAD** determinar el número máximo de bytes que se pueden leer con una **recepción** llamar desde este socket. El `lpArgument` parámetro señala a una `DWORD` en el que **IOCtl** almacena el resultado. Si este socket es de tipo **SOCK_STREAM**, **FIONREAD** devuelve la cantidad total de datos que se pueden leer en un único **recepción**; esto es normalmente el mismo que la cantidad total de datos en cola en el socket. Si este socket es de tipo **SOCK_DGRAM**, **FIONREAD** devuelve el tamaño del primer datagrama en cola en el socket.  
  
- **SIOCATMARK** determinar si se han leído todos los datos de fuera de banda. Esto se aplica sólo a un socket de tipo **SOCK_STREAM** que se ha configurado para la recepción en línea de datos fuera de banda ( **SO_OOBINLINE**). Si no hay datos fuera de banda está esperando a leer, la operación devuelve distinto de cero. De lo contrario devuelve 0 y el siguiente **recepción** o `ReceiveFrom` realizadas en el socket recuperará algunos o todos los datos anteriores a la "marca"; la aplicación debe utilizar el **SIOCATMARK** operación para determinar si los datos permanecen. Si hay datos normales antes de los datos (fuera de banda) "urgentes", se recibirán en orden. (Tenga en cuenta que un **recepción** o `ReceiveFrom` nunca se mezcle datos fuera de banda y normales en la misma llamada.) El `lpArgument` parámetro señala a una `DWORD` en el que **IOCtl** almacena el resultado.  
  
 Esta función es un subconjunto de **ioctl()** como utiliza en sockets Berkeley. En concreto, no hay ningún comando que es equivalente a **FIOASYNC**, mientras que **SIOCATMARK** es el comando solo de nivel de socket que se admite.  
  
##  <a name="a-namelistena--casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket:: Listen  
 Llame a esta función miembro para escuchar las solicitudes de conexión entrante.  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>Parámetros  
 *nConnectionBacklog*  
 La longitud máxima que puede alcanzar la cola de conexiones pendientes. Intervalo válido es de 1 a 5.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEADDRINUSE** se ha realizado un intento para escuchar en una dirección en uso.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEINVAL** el socket no se ha enlazado con **enlace** o ya está conectado.  
  
- **WSAEISCONN** el socket ya está conectado.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- `WSAENOBUFS`No hay espacio de búfer está disponible.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP** el socket que se hace referencia no es del tipo que admite la `Listen` operación.  
  
### <a name="remarks"></a>Comentarios  
 Para aceptar conexiones, el socket se crea por primera vez con **crear**, se especifica un trabajo pendiente para las conexiones entrantes con `Listen`, y, a continuación, se aceptan las conexiones con **Accept**. `Listen`se aplica sólo a sockets que admiten conexiones, es decir, los de tipo **SOCK_STREAM**. Este socket se coloca en modo "pasivo donde se confirma y en cola pendientes de aceptación, el proceso de las conexiones entrantes".  
  
 Esta función se utiliza normalmente a los servidores (o cualquier aplicación que desee aceptar conexiones) que podría tener más de una solicitud de conexión en un momento: si llega una solicitud de conexión con la cola completa, el cliente recibirá un error con una indicación de **WSAECONNREFUSED**.  
  
 `Listen`intenta seguir funcionando racional cuando no hay disponibles puertos (descriptores). Aceptará conexiones hasta que la cola está vacía. Si los puertos están disponibles, una llamada posterior a `Listen` o **Accept** se renueve la cola a la actual o más reciente "trabajo pendiente," si es posible y reanudar escuchar las conexiones entrantes.  
  
##  <a name="a-namemhsocketa--casyncsocketmhsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket  
 Contiene el **SOCKET** controlar para el socket encapsulado por este `CAsyncSocket` objeto.  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="a-nameonaccepta--casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAccept  
 Llamado por el marco de trabajo para notificar a un socket de escucha puede aceptar solicitudes de conexión pendientes llamando a la [Accept](#accept) función miembro.  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrorCode`  
 El error más reciente en un socket. Los siguientes códigos de error se aplica a la `OnAccept` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="a-nameonclosea--casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose  
 Llamado por el marco de trabajo para notificar a este socket que se cierra el socket conectado por su proceso.  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrorCode`  
 El error más reciente en un socket. Códigos de error siguientes se aplican a la `OnClose` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAECONNRESET** conexión restablecida por el lado remoto.  
  
- **WSAECONNABORTED** se anuló la conexión debido al tiempo de espera u otro error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="a-nameonconnecta--casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect  
 Llamado por el marco de trabajo para notificar al conectar el socket que su intento de conexión se ha completado, ya sea correctamente o en error.  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrorCode`  
 El error más reciente en un socket. Códigos de error siguientes se aplican a la `OnConnect` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAEADDRINUSE** la dirección especificada ya está en uso.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAECONNREFUSED** forzosamente se rechazó el intento de conexión.  
  
- **WSAEDESTADDRREQ** se requiere una dirección de destino.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento es incorrecto.  
  
- **WSAEINVAL** el socket ya está enlazado a una dirección.  
  
- **WSAEISCONN** el socket ya está conectado.  
  
- **WSAEMFILE** no hay más descriptores de archivo están disponibles.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
- `WSAENOBUFS`No hay espacio de búfer está disponible. No se puede conectar el socket.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor es un archivo, no es un socket.  
  
- **WSAETIMEDOUT** el intento de conexión agotó el tiempo de espera sin establecer una conexión.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  En [CSocket](../../mfc/reference/csocket-class.md), el `OnConnect` nunca se llama la función de notificación. Para las conexiones, simplemente llame **conectar**, lo cual devolverá cuando se complete la conexión (correctamente o error). Cómo se administran las notificaciones de conexión es un detalle de implementación de MFC.  
  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFCAsyncSocket](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="a-nameonoutofbanddataa--casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData  
 Llamado por el marco de trabajo para notificar al socket receptor que el socket emisor tiene datos fuera de banda para enviar.  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrorCode`  
 El error más reciente en un socket. Códigos de error siguientes se aplican a la `OnOutOfBandData` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
### <a name="remarks"></a>Comentarios  
 Datos fuera de banda están un canal lógicamente independiente que está asociado a cada par de sockets conectados de tipo **SOCK_STREAM**. El canal se utiliza generalmente para enviar datos urgentes.  
  
 MFC admite datos fuera de banda, pero los usuarios de la clase `CAsyncSocket` no se recomienda utilizarla. La manera más fácil es crear un segundo socket para transferir estos datos. Para obtener más información acerca de los datos fuera de banda, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="a-nameonreceivea--casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive  
 Llamado por el marco de trabajo para notificar a este socket que hay datos en el búfer que se puede recuperar mediante una llamada a la **recepción** función miembro.  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrorCode`  
 El error más reciente en un socket. Códigos de error siguientes se aplican a la `OnReceive` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAsyncSocket&#2;](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="a-nameonsenda--casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend  
 Llamado por el marco de trabajo para notificar el socket que puede enviar datos al llamar a la **enviar** función miembro.  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nErrorCode`  
 El error más reciente en un socket. Códigos de error siguientes se aplican a la `OnSend` función miembro:  
  
- **0** la función que se ejecutó correctamente.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: sockets de notificación](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAsyncSocket&3;](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="a-nameoperatoreqa--casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::operator =  
 Asigna un nuevo valor a un `CAsyncSocket` objeto.  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSrc`  
 Una referencia a un archivo `CAsyncSocket` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para copiar uno existente `CAsyncSocket` objeto a otro `CAsyncSocket` objeto.  
  
##  <a name="a-nameoperatorsocketa--casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::operator SOCKET  
 Utilice este operador para recuperar la **SOCKET** identificador de la `CAsyncSocket` objeto.  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador de la **SOCKET** objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar el controlador para llamar directamente a las API de Windows.  
  
##  <a name="a-namereceivea--casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Receive  
 Llame a esta función miembro para recibir datos de un socket.  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Un búfer para los datos entrantes.  
  
 `nBufLen`  
 La longitud de `lpBuf` en bytes.  
  
 `nFlags`  
 Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y `nFlags` parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ `OR` operador:  
  
- **MSG_PEEK** inspeccionar los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.  
  
- **MSG_OOB** procesar datos fuera de banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, **recepción** devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a **recepción** en un socket después `ShutDown` se ha invocado con `nHow` establecido en 0 ó 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la **recepción** operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.  
  
- **WSAEINVAL** el socket no se ha enlazado con **enlace**.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido al tiempo de espera u otro error.  
  
- **WSAECONNRESET** el circuito virtual se restableció por el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para la secuencia conectados o sockets de datagramas y se utiliza para leer los datos entrantes.  
  
 Para los sockets de tipo **SOCK_STREAM**, como se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket **SO_OOBINLINE**) y no se ha leído datos fuera de banda, se devolverán datos sólo fuera de banda. La aplicación puede utilizar el **IOCtlSIOCATMARK** opción o [OnOutOfBandData](#onoutofbanddata) para determinar si los datos de más de fuera de banda permanecen a leerse.  
  
 Para los sockets de datagramas, se extraen los datos desde el primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se llena con la primera parte del datagrama, el exceso de datos se pierde, y **recepción** devuelve un valor de **SOCKET_ERROR** con el código de error establecido en **WSAEMSGSIZE**. Si no hay datos entrantes están disponibles en el socket, un valor de **SOCKET_ERROR** se devuelve con el código de error establecido en **WSAEWOULDBLOCK**. El [OnReceive](#onreceive) función de devolución de llamada puede utilizarse para determinar cuándo llegan a más datos.  
  
 Si el socket es de tipo **SOCK_STREAM** y el lado remoto cerró la conexión correctamente, un **recepción** finalizará inmediatamente con 0 bytes recibidos. Si se ha restablecido la conexión, un **recepción** producirá el error **WSAECONNRESET**.  
  
 **Recibir** debe llamarse una vez por cada vez [CAsyncSocket::OnReceive](#onreceive) se llama.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="a-namereceivefroma--casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::ReceiveFrom  
 Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en el [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura o en `rSocketAddress`.  
  
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
 `lpBuf`  
 Un búfer para los datos entrantes.  
  
 `nBufLen`  
 La longitud de `lpBuf` en bytes.  
  
 `rSocketAddress`  
 Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.  
  
 `rSocketPort`  
 Hacer referencia a un **UINT** que almacena un puerto.  
  
 `lpSockAddr`  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección de origen tras la devolución.  
  
 `lpSockAddrLen`  
 Un puntero a la longitud de la dirección de origen `lpSockAddr` en bytes.  
  
 `nFlags`  
 Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y `nFlags` parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ `OR` operador:  
  
- **MSG_PEEK** inspeccionar los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.  
  
- **MSG_OOB** procesar datos fuera de banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `ReceiveFrom` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a `GetLastError`. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento no era válido: el `lpSockAddr` búfer es demasiado pequeño para dar cabida a la dirección del mismo nivel.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEINVAL** el socket no se ha enlazado con **enlace**.  
  
- **WSAENOTCONN** el socket no conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `ReceiveFrom` en un socket después `ShutDown` se ha invocado con `nHow` establecido en 0 ó 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la `ReceiveFrom` operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido al tiempo de espera u otro error.  
  
- **WSAECONNRESET** el circuito virtual se restableció por el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.  
  
 Para controlar las direcciones IPv6, utilice [CAsyncSocket::ReceiveFromEx](#receivefromex).  
  
 Para los sockets de tipo **SOCK_STREAM**, como se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket **SO_OOBINLINE**) y no se ha leído datos fuera de banda, se devolverán datos sólo fuera de banda. La aplicación puede utilizar el **IOCtlSIOCATMARK** opción o `OnOutOfBandData` para determinar si los datos de más de fuera de banda permanecen a leerse. El `lpSockAddr` y `lpSockAddrLen` se omiten los parámetros de **SOCK_STREAM** sockets.  
  
 Para los sockets de datagramas, se extraen los datos desde el primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se llena con la primera parte del mensaje, el exceso de datos se pierde, y `ReceiveFrom` devuelve un valor de **SOCKET_ERROR** con el código de error establecido en **WSAEMSGSIZE**.  
  
 Si `lpSockAddr` es distinto de cero, y el socket es de tipo **SOCK_DGRAM**, la dirección de red del socket que envió la información se copia en el correspondiente [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura. El valor indicado por `lpSockAddrLen` se inicializa en el tamaño de esta estructura y se modifica en el valor devuelto para indicar el tamaño real de la dirección que se almacenan allí. Si no hay datos entrantes están disponibles en el socket, la `ReceiveFrom` llamada espera a que lleguen a menos que el socket de datos no sea de bloqueo. En este caso, un valor de **SOCKET_ERROR** se devuelve con el código de error establecido en **WSAEWOULDBLOCK**. El `OnReceive` devolución de llamada puede utilizarse para determinar cuándo llegan a más datos.  
  
 Si el socket es de tipo **SOCK_STREAM** y el lado remoto cerró la conexión correctamente, un `ReceiveFrom` finalizará inmediatamente con 0 bytes recibidos.  
  
##  <a name="a-namereceivefromexa--casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx  
 Llame a esta función miembro para recibir un datagrama y almacenar la dirección de origen en el [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura o en `rSocketAddress` (controla direcciones IPv6).  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Un búfer para los datos entrantes.  
  
 `nBufLen`  
 La longitud de `lpBuf` en bytes.  
  
 `rSocketAddress`  
 Hacer referencia a un `CString` objeto que recibe la dirección IP numérica con puntos.  
  
 `rSocketPort`  
 Hacer referencia a un **UINT** que almacena un puerto.  
  
 `nFlags`  
 Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y `nFlags` parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ `OR` operador:  
  
- **MSG_PEEK** inspeccionar los datos entrantes. Los datos se copian en el búfer, pero no se quitan de la cola de entrada.  
  
- **MSG_OOB** procesar datos fuera de banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `ReceiveFromEx` devuelve el número de bytes recibidos. Si se ha cerrado la conexión, devuelve 0. De lo contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a `GetLastError`. Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** el `lpSockAddrLen` argumento no era válido: el `lpSockAddr` búfer es demasiado pequeño para dar cabida a la dirección del mismo nivel.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEINVAL** el socket no se ha enlazado con **enlace**.  
  
- **WSAENOTCONN** el socket no conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `ReceiveFromEx` en un socket después `ShutDown` se ha invocado con `nHow` establecido en 0 ó 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la `ReceiveFromEx` operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el datagrama es demasiado grande para caber en el búfer especificado y se ha truncado.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido al tiempo de espera u otro error.  
  
- **WSAECONNRESET** el circuito virtual se restableció por el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para leer los datos entrantes en un socket (posiblemente conectado) y capturar la dirección desde la que se enviaron los datos.  
  
 Esta función es el mismo que [CAsyncSocket::ReceiveFrom](#receivefrom) salvo que controla IPv6 direcciones protocolos así como antiguos.  
  
 Para los sockets de tipo **SOCK_STREAM**, como se devuelve toda la información está disponible hasta el tamaño del búfer proporcionado. Si el socket se ha configurado para la recepción en línea de datos fuera de banda (opción de socket **SO_OOBINLINE**) y no se ha leído datos fuera de banda, se devolverán datos sólo fuera de banda. La aplicación puede utilizar el **IOCtlSIOCATMARK** opción o `OnOutOfBandData` para determinar si los datos de más de fuera de banda permanecen a leerse. El `lpSockAddr` y `lpSockAddrLen` se omiten los parámetros de **SOCK_STREAM** sockets.  
  
 Para los sockets de datagramas, se extraen los datos desde el primer datagrama en cola, hasta el tamaño del búfer proporcionado. Si el datagrama es mayor que el búfer proporcionado, el búfer se llena con la primera parte del mensaje, el exceso de datos se pierde, y `ReceiveFromEx` devuelve un valor de **SOCKET_ERROR** con el código de error establecido en **WSAEMSGSIZE**.  
  
 Si `lpSockAddr` es distinto de cero, y el socket es de tipo **SOCK_DGRAM**, la dirección de red del socket que envió la información se copia en el correspondiente [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura. El valor indicado por `lpSockAddrLen` se inicializa en el tamaño de esta estructura y se modifica en el valor devuelto para indicar el tamaño real de la dirección que se almacenan allí. Si no hay datos entrantes están disponibles en el socket, la `ReceiveFromEx` llamada espera a que lleguen a menos que el socket de datos no sea de bloqueo. En este caso, un valor de **SOCKET_ERROR** se devuelve con el código de error establecido en **WSAEWOULDBLOCK**. El `OnReceive` devolución de llamada puede utilizarse para determinar cuándo llegan a más datos.  
  
 Si el socket es de tipo **SOCK_STREAM** y el lado remoto cerró la conexión correctamente, un `ReceiveFromEx` finalizará inmediatamente con 0 bytes recibidos.  
  
##  <a name="a-namesenda--casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Send  
 Llame a esta función miembro para enviar datos en un socket conectado.  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Búfer que contiene los datos que se transmitan.  
  
 `nBufLen`  
 La longitud de los datos de `lpBuf` en bytes.  
  
 `nFlags`  
 Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y `nFlags` parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ `OR` operador:  
  
- **MSG_DONTROUTE** especifica que los datos no deben ser susceptible de enrutamiento. Puede elegir un proveedor de Windows Sockets pasar por alto este indicador.  
  
- **MSG_OOB** enviar datos fuera de banda ( **SOCK_STREAM** solo).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, **enviar** devuelve el número total de caracteres que se envían. (Tenga en cuenta que puede ser menor que el número indicado por `nBufLen`.) De lo contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEACCES** la dirección solicitada es una dirección de difusión, pero no se ha establecido el marcador adecuado.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEFAULT** el `lpBuf` argumento no es una parte del espacio de direcciones de usuario válida.  
  
- **WSAENETRESET** se debe restablecer la conexión porque la implementación de Windows Sockets quitó.  
  
- `WSAENOBUFS`La implementación de Windows Sockets notifica un interbloqueo de búfer.  
  
- **WSAENOTCONN** el socket no está conectado.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a **enviar** en un socket después `ShutDown` se ha invocado con `nHow` establecido en 1 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el socket es de tipo **SOCK_DGRAM**, y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.  
  
- **WSAEINVAL** el socket no se ha enlazado con **enlace**.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido al tiempo de espera u otro error.  
  
- **WSAECONNRESET** el circuito virtual se restableció por el lado remoto.  
  
### <a name="remarks"></a>Comentarios  
 **Enviar** se utiliza para escribir los datos salientes en los sockets de datagramas o la secuencia conectados. Para los sockets de datagramas, se debe tener cuidado de no debe exceder el tamaño máximo de paquetes IP de las subredes subyacentes, que viene determinado por la **iMaxUdpDg** el elemento en el [WSADATA](../../mfc/reference/wsadata-structure.md) estructura devuelta por `AfxSocketInit`. Si los datos están demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error **WSAEMSGSIZE** se devuelve a través de `GetLastError`, y se transmite ningún dato.  
  
 Tenga en cuenta que para un datagrama socket la realización correcta de un **enviar** no indica que se ha entregado correctamente los datos.  
  
 En `CAsyncSocket` objetos de tipo **SOCK_STREAM**, el número de bytes escritos puede estar entre 1 y la longitud solicitada, dependiendo de la disponibilidad de búfer en los hosts locales y externos.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAsyncSocket::OnSend](#onsend).  
  
##  <a name="a-namesendtoa--casyncsocketsendto"></a><a name="sendto"></a>:: SendTo  
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
 `lpBuf`  
 Búfer que contiene los datos que se transmitan.  
  
 `nBufLen`  
 La longitud de los datos de `lpBuf` en bytes.  
  
 `nHostPort`  
 El puerto identifica la aplicación de socket.  
  
 `lpszHostAddress`  
 La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número de puntos, como "128.56.22.8".  
  
 `nFlags`  
 Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y `nFlags` parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ `OR` operador:  
  
- **MSG_DONTROUTE** especifica que los datos no deben ser susceptible de enrutamiento. Puede elegir un proveedor de Windows Sockets pasar por alto este indicador.  
  
- **MSG_OOB** enviar datos fuera de banda ( **SOCK_STREAM** solo).  
  
 `lpSockAddr`  
 Un puntero a un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura que contiene la dirección de socket de destino.  
  
 `nSockAddrLen`  
 La longitud de la dirección en `lpSockAddr` en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `SendTo` devuelve el número total de caracteres que se envían. (Tenga en cuenta que puede ser menor que el número indicado por `nBufLen`.) De lo contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEACCES** la dirección solicitada es una dirección de difusión, pero no se ha establecido el marcador adecuado.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEFAULT** el `lpBuf` o `lpSockAddr` parámetros no forman parte del espacio de direcciones del usuario, o la `lpSockAddr` argumento es demasiado pequeño (menor que el tamaño de una [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINVAL** el nombre de host no es válido.  
  
- **WSAENETRESET** se debe restablecer la conexión porque la implementación de Windows Sockets quitó.  
  
- `WSAENOBUFS`La implementación de Windows Sockets notifica un interbloqueo de búfer.  
  
- **WSAENOTCONN** el socket no conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `SendTo` en un socket después `ShutDown` se ha invocado con `nHow` establecido en 1 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el socket es de tipo **SOCK_DGRAM**, y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido al tiempo de espera u otro error.  
  
- **WSAECONNRESET** el circuito virtual se restableció por el lado remoto.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAEDESTADDRREQ** se requiere una dirección de destino.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
### <a name="remarks"></a>Comentarios  
 `SendTo`se utiliza en los sockets de datagramas o la secuencia y se utiliza para escribir los datos salientes en un socket. Para los sockets de datagramas, se debe tener cuidado de no debe exceder el tamaño máximo de paquetes IP de las subredes subyacentes, que viene determinado por la **iMaxUdpDg** el elemento en el [WSADATA](../../mfc/reference/wsadata-structure.md) estructura rellena [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos están demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error **WSAEMSGSIZE** se devuelve, y se transmite ningún dato.  
  
 Tenga en cuenta que la realización correcta de un `SendTo` no indica que se ha entregado correctamente los datos.  
  
 `SendTo`sólo se utiliza en una **SOCK_DGRAM** socket para enviar un datagrama a un socket específico identificado por el `lpSockAddr` parámetro.  
  
 Para enviar una difusión (en un **SOCK_DGRAM** sólo), la dirección en la `lpSockAddr` parámetro debe crearse utilizando la dirección IP especial **INADDR_BROADCAST** (definido en el archivo de encabezado de Windows Sockets WINSOCK. (H) junto con el número de puerto deseado. O bien, si la `lpszHostAddress` parámetro es **NULL**, el socket está configurado para la difusión. No es recomendable generalmente para un datagrama difusión supere el tamaño en el que puede producirse fragmentación, lo que implica que la parte de datos del datagrama (sin incluir los encabezados) no debe superar los 512 bytes.  
  
 Para controlar las direcciones IPv6, utilice [CAsyncSocket::SendToEx](#sendtoex).  
  
##  <a name="a-namesendtoexa--casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToEx  
 Llame a esta función miembro para enviar datos a un destino concreto (controla direcciones IPv6).  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Búfer que contiene los datos que se transmitan.  
  
 `nBufLen`  
 La longitud de los datos de `lpBuf` en bytes.  
  
 `nHostPort`  
 El puerto identifica la aplicación de socket.  
  
 `lpszHostAddress`  
 La dirección de red del socket al que está conectado este objeto: un nombre de equipo, como "ftp.microsoft.com" o un número de puntos, como "128.56.22.8".  
  
 `nFlags`  
 Especifica la manera en que se realiza la llamada. La semántica de esta función se determina mediante las opciones de socket y `nFlags` parámetro. Se construye mediante la combinación de cualquiera de los siguientes valores con C++ `OR` operador:  
  
- **MSG_DONTROUTE** especifica que los datos no deben ser susceptible de enrutamiento. Puede elegir un proveedor de Windows Sockets pasar por alto este indicador.  
  
- **MSG_OOB** enviar datos fuera de banda ( **SOCK_STREAM** solo).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se produce ningún error, `SendToEx` devuelve el número total de caracteres que se envían. (Tenga en cuenta que puede ser menor que el número indicado por `nBufLen`.) De lo contrario, un valor de **SOCKET_ERROR** se devuelve, y un código de error específico que se puede recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEACCES** la dirección solicitada es una dirección de difusión, pero no se ha establecido el marcador adecuado.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEFAULT** el `lpBuf` o `lpSockAddr` parámetros no forman parte del espacio de direcciones del usuario, o la `lpSockAddr` argumento es demasiado pequeño (menor que el tamaño de una [SOCKADDR](../../mfc/reference/sockaddr-structure.md) estructura).  
  
- **WSAEINVAL** el nombre de host no es válido.  
  
- **WSAENETRESET** se debe restablecer la conexión porque la implementación de Windows Sockets quitó.  
  
- `WSAENOBUFS`La implementación de Windows Sockets notifica un interbloqueo de búfer.  
  
- **WSAENOTCONN** el socket no conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
- **WSAEOPNOTSUPP MSG_OOB** se ha especificado, pero el socket no es de tipo **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** se cerró el socket; no es posible llamar a `SendToEx` en un socket después `ShutDown` se ha invocado con `nHow` establecido en 1 o 2.  
  
- **WSAEWOULDBLOCK** el socket se marca como no sea de bloqueo y la operación causaría un bloqueo.  
  
- **WSAEMSGSIZE** el socket es de tipo **SOCK_DGRAM**, y el datagrama es mayor que el máximo admitido por la implementación de Windows Sockets.  
  
- **WSAECONNABORTED** el circuito virtual se anuló debido al tiempo de espera u otro error.  
  
- **WSAECONNRESET** el circuito virtual se restableció por el lado remoto.  
  
- **WSAEADDRNOTAVAIL** la dirección especificada no está disponible en el equipo local.  
  
- **WSAEAFNOSUPPORT** direcciones de la familia especificada no se puede usar con este socket.  
  
- **WSAEDESTADDRREQ** se requiere una dirección de destino.  
  
- **WSAENETUNREACH** no se puede alcanzar la red desde este host en este momento.  
  
### <a name="remarks"></a>Comentarios  
 Este método es el mismo que [:: SendTo](#sendto) salvo que controla IPv6 direcciones protocolos así como antiguos.  
  
 `SendToEx`se utiliza en los sockets de datagramas o la secuencia y se utiliza para escribir los datos salientes en un socket. Para los sockets de datagramas, se debe tener cuidado de no debe exceder el tamaño máximo de paquetes IP de las subredes subyacentes, que viene determinado por la **iMaxUdpDg** el elemento en el [WSADATA](../../mfc/reference/wsadata-structure.md) estructura rellena [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si los datos están demasiado largos para pasar de forma atómica a través del protocolo subyacente, el error **WSAEMSGSIZE** se devuelve, y se transmite ningún dato.  
  
 Tenga en cuenta que la realización correcta de un `SendToEx` no indica que se ha entregado correctamente los datos.  
  
 `SendToEx`sólo se utiliza en una **SOCK_DGRAM** socket para enviar un datagrama a un socket específico identificado por el `lpSockAddr` parámetro.  
  
 Para enviar una difusión (en un **SOCK_DGRAM** sólo), la dirección en la `lpSockAddr` parámetro debe crearse utilizando la dirección IP especial **INADDR_BROADCAST** (definido en el archivo de encabezado de Windows Sockets WINSOCK. (H) junto con el número de puerto deseado. O bien, si la `lpszHostAddress` parámetro es **NULL**, el socket está configurado para la difusión. No es recomendable generalmente para un datagrama difusión supere el tamaño en el que puede producirse fragmentación, lo que implica que la parte de datos del datagrama (sin incluir los encabezados) no debe superar los 512 bytes.  
  
##  <a name="a-namesetsockopta--casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockOpt  
 Llame a esta función miembro para establecer una opción de socket.  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parámetros  
 `nOptionName`  
 La opción de socket para los que el valor va a establecerse.  
  
 `lpOptionValue`  
 Un puntero al búfer en el que se proporciona el valor de la opción solicitada.  
  
 `nOptionLen`  
 El tamaño de la `lpOptionValue` búfer en bytes.  
  
 `nLevel`  
 El nivel en el que se define la opción; los niveles admitidos sólo son **SOL_SOCKET** y **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEFAULT** `lpOptionValue` no es una parte válida del espacio de direcciones del proceso.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAEINVAL** `nLevel` no es válido, o la información de `lpOptionValue` no es válido.  
  
- **WSAENETRESET** conexión ha agotado cuando **SO_KEEPALIVE** se establece.  
  
- **WSAENOPROTOOPT** la opción es desconocido o no compatible. En particular, **SO_BROADCAST** no se admite en sockets de tipo **SOCK_STREAM**, mientras que **SO_DONTLINGER**, **SO_KEEPALIVE**, **SO_LINGER**, y **SO_OOBINLINE** no se admite en sockets de tipo **SOCK_DGRAM**.  
  
- **WSAENOTCONN** conexión ha sido restablecer cuando **SO_KEEPALIVE** se establece.  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 `SetSockOpt`establece el valor actual de una opción de socket asociado a un socket de cualquier tipo, en cualquier estado. Aunque pueden existir opciones en varios niveles de protocolo, esta especificación sólo define opciones que existen en el nivel superior "socket". Opciones afectan a las operaciones de socket, como si se recepción datos inmediatos en el flujo normal de datos, si el socket pueden enviar mensajes de difusión y así sucesivamente.  
  
 Hay dos tipos de opciones de socket: opciones booleanas que habilitar o deshabilitación una característica o el comportamiento y las opciones que requieren una estructura o un valor entero. Para habilitar una opción de booleana `lpOptionValue` apunta a un entero distinto de cero. Para deshabilitar la opción `lpOptionValue` apunta a un entero igual a cero. `nOptionLen`debe ser igual a **sizeof (bool)** para opciones booleanas. Para otras opciones, `lpOptionValue` apunta al entero o estructura que contiene el valor deseado para la opción y `nOptionLen` es la longitud de la estructura o un entero.  
  
 **SO_LINGER** la acción realizada cuando no enviado los datos en la cola en un socket de controles y la **cerrar** función se invoca para cerrar el socket.  
  
 De forma predeterminada, no se puede enlazar un socket (consulte [enlace](#bind)) a una dirección local que ya está en uso. En ocasiones, sin embargo, puede ser deseable "reutilizar" una dirección de esta manera. Puesto que todas las conexiones se identifican mediante la combinación de direcciones locales y remotas, no hay ningún problema de tener dos sockets enlazados a la misma dirección local, como las direcciones remotas son diferentes.  
  
 Para informar a la implementación de Windows Sockets que un **enlazar** llamada en un socket que no se pueden bloquear porque la dirección deseada ya está en uso por otro socket, la aplicación debe establecer el **SO_REUSEADDR** socket opción para el socket antes de emitir la **enlazar** llamar. Tenga en cuenta que la opción se interpreta sólo en el momento de la **enlazar** llamar: por lo tanto, es necesario (pero inofensivo) establecer la opción en un socket que no esté enlazado a una dirección existente, y establecer o restablecer la opción después de la **enlazar** llamada no tiene ningún efecto en este o cualquier otro tipo de socket.  
  
 Una aplicación puede solicitar que la implementación de Windows Sockets habilitar el uso de paquetes "keep-alive" en las conexiones de protocolo de Control de transmisión (TCP) activando la **SO_KEEPALIVE** opción de socket. Una implementación de Windows Sockets no necesita admitir el uso de abiertas: si lo hace, la semántica precisa son específicos de la implementación, pero debe ajustarse a la sección 4.2.3.6 de RFC 1122: "requisitos para Hosts de Internet: niveles de comunicación." Si se interrumpe una conexión como resultado de "abiertas" el código de error **WSAENETRESET** se devuelve a las llamadas en curso en el socket, y las subsiguientes llamadas se producirá un error con **WSAENOTCONN**.  
  
 El **TCP_NODELAY** opción deshabilita el algoritmo de Nagle. El algoritmo de Nagle se utiliza para reducir el número de pequeños paquetes enviados por un host mediante el almacenamiento en búfer de datos no confirmados de envío hasta que puede enviarse un paquete de tamaño completo. Sin embargo, para algunas aplicaciones de este algoritmo puede reducir el rendimiento, y **TCP_NODELAY** puede utilizarse para desactivarlo. Escritores de aplicación no deben establecer **TCP_NODELAY** a menos que el efecto de hacerlo es claros y deseado, desde la configuración **TCP_NODELAY** puede tener un efecto negativo importante en el rendimiento de la red. **Tcp_nodelay** es el único admite la opción de socket que usa un nivel de **IPPROTO_TCP**; todas las demás opciones utilizan nivel **SOL_SOCKET**.  
  
 Algunas implementaciones de la oferta de Windows Sockets genere información de depuración si el **SO_DEBUG** opción está establecida por una aplicación.  
  
 Se admiten las siguientes opciones para `SetSockOpt`. El tipo identifica el tipo de datos dirigidos por `lpOptionValue`.  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|Permitir la transmisión de mensajes de difusión en el socket.|  
|**SO_DEBUG**|**BOOL**|Registra información de depuración.|  
|**SO_DONTLINGER**|**BOOL**|No bloquear **cerrar** esperando los datos que se envían. Esta opción es equivalente a establecer **SO_LINGER** con **l_onoff** establecido en cero.|  
|**SO_DONTROUTE**|**BOOL**|No enrutar: enviar directamente a la interfaz.|  
|**SO_KEEPALIVE**|**BOOL**|Enviar keepalive.|  
|**SO_LINGER**|**struct LINGER**|Demora **cerrar** si no enviado los datos están presentes.|  
|**SO_OOBINLINE**|**BOOL**|Recibir datos fuera de banda en el flujo normal de datos.|  
|**SO_RCVBUF**|`int`|Especifique recibe el tamaño del búfer.|  
|**SO_REUSEADDR**|**BOOL**|Permitir que el socket esté enlazado a una dirección que ya está en uso. (See [Bind](#bind).)|  
|**SO_SNDBUF**|`int`|Especificar el tamaño de búfer para los envíos.|  
|**TCP_NODELAY**|**BOOL**|Deshabilita el algoritmo de Nagle para la fusión de envíos.|  
  
 Opciones de Berkeley Software Distribution (BSD) no se admite para `SetSockOpt` son:  
  
|Valor|Tipo|Significado|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Socket de escucha|  
|**SO_ERROR**|`int`|Obtiene el estado de error y borra.|  
|**SO_RCVLOWAT**|`int`|Recibir marca de agua suave.|  
|**SO_RCVTIMEO**|`int`|Tiempo de espera de recepción|  
|**SO_SNDLOWAT**|`int`|Enviar la marca de agua suave.|  
|**SO_SNDTIMEO**|`int`|Tiempo de espera de envío.|  
|**SO_TYPE**|`int`|Tipo del socket.|  
|**IP_OPTIONS**||Establezca el campo de opciones en el encabezado IP.|  
  
##  <a name="a-nameshutdowna--casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::ShutDown  
 Llamada a esta función miembro para deshabilitar envía, recibe, o ambos en el socket.  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>Parámetros  
 `nHow`  
 Una marca que describe qué tipos de operación ya no se permitirá, mediante los valores enumerados siguientes:  
  
- **recibe = 0**  
  
- **envía = 1**  
  
- **tanto = 2**  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a [GetLastError](#getlasterror). Los errores siguientes se aplican a esta función miembro:  
  
- **WSANOTINITIALISED** correcta [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) debe producirse antes de utilizar esta API.  
  
- **WSAENETDOWN** implementación de los Sockets de Windows ha detectado que el subsistema de red no pudo.  
  
- **WSAEINVAL** `nHow` no es válido.  
  
- **WSAEINPROGRESS** está en curso una operación bloqueo de Windows Sockets.  
  
- **WSAENOTCONN** el socket no conectado ( **SOCK_STREAM** solo).  
  
- **WSAENOTSOCK** el descriptor no es un socket.  
  
### <a name="remarks"></a>Comentarios  
 `ShutDown`se utiliza en todos los tipos de sockets para deshabilitar la recepción, transmisión o ambos. Si `nHow` es 0, recibe subsiguientes en el socket se deshabilitará. Esto no tiene ningún efecto en las capas de protocolo inferiores.  
  
 Protocolo de Control de transmisión (TCP), no se cambia la ventana TCP y los datos entrantes serán aceptados (pero no confirmado) hasta que se agote la ventana. Protocolo de datagramas de usuario (UDP), los datagramas entrantes aceptados y en cola. En ningún caso se generará un paquete de error ICMP. Si `nHow` es 1, no se permiten los envíos posteriores. Para los sockets TCP, se enviará un FIN. Establecer `nHow` a 2 deshabilita tanto los envíos y recepciones como se describió anteriormente.  
  
 Tenga en cuenta que `ShutDown` no cerrar el socket y los recursos adjuntados al socket no se liberarán hasta que **cerrar** se llama. Una aplicación no debe confiar en poder reutilizar un socket después de que se ha cerrado. En concreto, una implementación de Windows Sockets no es necesario para admitir el uso de **conectar** en un socket de este tipo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="a-namesocketa--casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Socket  
 Asigna un identificador de socket.  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSocketType`  
 Especifica `SOCK_STREAM` o `SOCK_DGRAM`.  
  
 `lEvent`  
 Máscara de bits que especifica una combinación de eventos de red en el que está interesada la aplicación.  
  
- `FD_READ`: Desea recibir una notificación de preparación para la lectura.  
  
- `FD_WRITE`: Desea recibir una notificación de preparación para la escritura.  
  
- `FD_OOB`: Desea recibir una notificación de la llegada de datos fuera de banda.  
  
- `FD_ACCEPT`: Desea recibir una notificación de las conexiones entrantes.  
  
- `FD_CONNECT`: Desea recibir una notificación de conexión completa.  
  
- `FD_CLOSE`: Desea recibir una notificación de cierre del socket.  
  
 `nProtocolType`  
 Protocolo que se usará con el socket que es específico de la familia de la dirección indicada.  
  
 `nAddressFormat`  
 Especificación para la familia de direcciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la operación se realiza correctamente; de lo contrario, devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método asigna un identificador de socket. No llamar [CAsyncSocket::Bind](#bind) para enlazar el socket a una dirección especificada, por lo que debe llamar a `Bind` más adelante para enlazar el socket a una dirección especificada. Puede usar [CAsyncSocket::SetSockOpt](#setsockopt) para establecer la opción de socket antes del enlace.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CSocket (clase)](../../mfc/reference/csocket-class.md)   
 [Clase CSocketFile](../../mfc/reference/csocketfile-class.md)

