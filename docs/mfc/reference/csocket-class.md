---
title: CSocket (clase)
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266567"
---
# <a name="csocket-class"></a>CSocket (clase)

Se deriva de `CAsyncSocket`, hereda la encapsulación de la API de Windows Sockets y representa un mayor nivel de abstracción que de un `CAsyncSocket` objeto.

## <a name="syntax"></a>Sintaxis

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Construye un objeto `CSocket`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSocket::Attach](#attach)|Asocia un identificador de SOCKET a un `CSocket` objeto.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Cancela una llamada de bloqueo que está actualmente en curso.|
|[CSocket::Create](#create)|Crea un socket.|
|[CSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CSocket` objeto, dado un identificador de SOCKET.|
|[CSocket::IsBlocking](#isblocking)|Determina si una llamada de bloqueo está en curso.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Se llama para procesar los mensajes pendientes mientras se esperaba una llamada de bloqueo en completarse.|

## <a name="remarks"></a>Comentarios

`CSocket` funciona con las clases `CSocketFile` y `CArchive` para administrar el envío y recepción de datos.

Un `CSocket` objeto también proporciona bloqueo, lo cual es esencial para la operación sincrónica de `CArchive`. Bloqueo de las funciones, como `Receive`, `Send`, `ReceiveFrom`, `SendTo`, y `Accept` (heredar todos los `CAsyncSocket`), no devuelven un `WSAEWOULDBLOCK` error en `CSocket`. En su lugar, estas funciones espere hasta que se complete la operación. Además, se terminará la llamada original con el error WSAEINTR si `CancelBlockingCall` se llama mientras se está bloqueando una de estas funciones.

Para usar un `CSocket` de objeto, llame al constructor, a continuación, llame a `Create` para crear el identificador SOCKET subyacente (tipo de SOCKET). Los parámetros predeterminados de `Create` crear un socket de secuencia, pero si no está utilizando el socket con un `CArchive` objeto, puede especificar un parámetro para crear un socket de datagrama en su lugar, o enlazar a un puerto específico para crear un socket de servidor. Conectarse a un socket de cliente con `Connect` en el lado cliente y `Accept` en el servidor. A continuación, cree un `CSocketFile` objeto y asociarlo a la `CSocket` objeto en el `CSocketFile` constructor. A continuación, cree un `CArchive` objeto para el envío y otro para recibir los datos (según sea necesario), a continuación, asociar con el `CSocketFile` objeto en el `CArchive` constructor. Cuando finalizan las comunicaciones, destruir la `CArchive`, `CSocketFile`, y `CSocket` objetos. El tipo de datos SOCKET se describe en el artículo [Windows Sockets: en segundo plano](../../mfc/windows-sockets-background.md).

Cuando usas `CArchive` con `CSocketFile` y `CSocket`, pueda encontrar una situación donde `CSocket::Receive` entra en un bucle (por `PumpMessages(FD_READ)`) a la espera para la cantidad de bytes solicitada. Esto es debido a que los sockets de Windows permiten sólo una llamada de recepción por notificación FD_READ, pero `CSocketFile` y `CSocket` permitir varias llamadas recibidas por FD_READ. Si recibe un FD_READ cuando no hay ningún dato para leer, la aplicación se bloquea. Si nunca se produce otra FD_READ, la aplicación deja de comunicarse a través del socket.

Puede resolver este problema como se indica a continuación. En el `OnReceive` método de la clase socket, llamada `CAsyncSocket::IOCtl(FIONREAD, ...)` antes de llamar a la `Serialize` método de la clase de mensaje cuando los datos esperados para leerse desde el socket superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red Normalmente, al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a todos los datos se reciben y solo después inicia la operación de lectura.

En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte en el código.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Cuando se usa sockets MFC en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se llama sólo en el subproceso principal.

Para obtener más información, consulte [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: Cómo funcionan los Sockets con archivos](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: Secuencia de operaciones](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: Ejemplo de Sockets que usan archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsock.h

##  <a name="attach"></a>  CSocket::Attach

Llame a esta función miembro para adjuntar el `hSocket` identificador de un `CSocket` objeto.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador a un socket.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente.

### <a name="remarks"></a>Comentarios

El identificador de SOCKET se almacena en el objeto [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) miembro de datos.

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

Llame a esta función miembro para cancelar una llamada de bloqueo actualmente en curso.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Comentarios

Esta función cancela cualquier operación de bloqueo pendiente para este socket. La llamada de bloqueo original se terminará tan pronto como sea posible con el error WSAEINTR.

En el caso de un bloqueo `Connect` , la implementación de Windows Sockets finalizará la operación la llamada de bloqueo tan pronto como sea posible, pero puede no ser posible para los recursos de socket para liberarse hasta que la conexión ha finalizado (y, a continuación, se ha restablecido) o tiempo de espera. Esto es probable que sean evidentes sólo si la aplicación intenta inmediatamente para abrir un nuevo socket (si no hay sockets disponibles), o para conectar con el mismo nodo.

Cancelar cualquier operación distinta `Accept` puede dejar el socket en un estado indeterminado. Si una aplicación cancela una operación de bloqueo en un socket, la única operación que puede depender de la aplicación que se va a llevar a cabo en el socket es una llamada a `Close`, aunque otras operaciones pueden funcionar en algunas implementaciones de Windows Sockets. Si desea maximizar la portabilidad de la aplicación, debe ser cuidado de no dependen de realizar operaciones después de una cancelación.

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>  CSocket::Create

Llame a la **crear** función miembro después de crear un objeto de socket para crear el socket de Windows y adjuntarlo.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
Un puerto determinado para su uso con el socket, o 0 si desea que MFC para seleccionar un puerto.

*nSocketType*<br/>
SOCK_STREAM o SOCK_DGRAM.

*lpszSocketAddress*<br/>
Un puntero a una cadena que contiene la dirección de red del socket conectado, un número separado por puntos, como "128.56.22.8". Pasar el valor NULL de cadena para este parámetro indica el `CSocket` instancia debe escuchar la actividad del cliente en todas las interfaces de red.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a `GetLastError`.

### <a name="remarks"></a>Comentarios

`Create` a continuación, llama a `Bind` para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:

- SOCK_STREAM proporciona secuenciado, secuencias de bytes bidireccionales confiables, basadas en conexión. Usa el protocolo de Control de transmisión (TCP) para la familia de direcciones de Internet.

- SOCK_DGRAM admite datagramas, que están sin conexión y no confiables de los búferes de longitud máxima fija (normalmente corta). Usa el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet. Para usar esta opción, no debe utilizar el socket con un `CArchive` objeto.

    > [!NOTE]
    >  El `Accept` función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. No llame a `Create` para este nuevo objeto de socket.

Para obtener más información acerca de los sockets de datagrama y de secuencia, consulte los artículos [Windows Sockets: En segundo plano](../../mfc/windows-sockets-background.md), [Windows Sockets: Puertos y direcciones de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md), y [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>  CSocket::CSocket

Construye un objeto `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Comentarios

Después de la construcción, debe llamar a la `Create` función miembro.

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>  CSocket::FromHandle

Devuelve un puntero a un `CSocket` objeto.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador a un socket.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CSocket` de objeto, o NULL si no existe ningún `CSocket` objeto asociado al *hSocket*.

### <a name="remarks"></a>Comentarios

Cuando se especifica un identificador de SOCKET, si un `CSocket` objeto no está asociado al identificador, la función miembro devuelve NULL y no crea un objeto temporal.

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>  CSocket::IsBlocking

Llame a esta función miembro para determinar si una llamada de bloqueo está en curso.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el socket está bloqueando; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

Reemplace esta función miembro para buscar mensajes concretos de Windows y responder a ellos en el socket.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha controlado el mensaje; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esto es un avanzado que se puede invalidar.

Las llamadas de framework `OnMessagePending` mientras el socket suministra mensajes de Windows para ofrecerle una oportunidad para tratar con mensajes que le interesen a la aplicación. Para obtener ejemplos de cómo puede usar `OnMessagePending`, consulte el artículo [Windows Sockets: Derivación de clases de Socket](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Vea también

[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
