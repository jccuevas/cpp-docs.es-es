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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854590"
---
# <a name="csocket-class"></a>CSocket (clase)

Deriva de `CAsyncSocket`, hereda su encapsulación de la API de Windows Sockets y representa un nivel más alto de abstracción que el de un objeto `CAsyncSocket`.

## <a name="syntax"></a>Sintaxis

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSocket:: CSocket](#csocket)|Construye un objeto `CSocket`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSocket:: Attach](#attach)|Asocia un identificador de SOCKET a un objeto `CSocket`.|
|[CSocket:: CancelBlockingCall](#cancelblockingcall)|Cancela una llamada de bloqueo que está actualmente en curso.|
|[CSocket:: Create](#create)|Crea un socket.|
|[CSocket:: FromHandle](#fromhandle)|Devuelve un puntero a un objeto `CSocket`, dado un identificador de SOCKET.|
|[CSocket:: IsBlocking](#isblocking)|Determina si hay una llamada de bloqueo en curso.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CSocket:: OnMessagePending](#onmessagepending)|Se llama para procesar los mensajes pendientes mientras se espera a que se complete una llamada de bloqueo.|

## <a name="remarks"></a>Observaciones

`CSocket` funciona con clases `CSocketFile` y `CArchive` para administrar el envío y la recepción de datos.

Un objeto `CSocket` también proporciona bloqueo, que es fundamental para el funcionamiento sincrónico de `CArchive`. Las funciones de bloqueo, como `Receive`, `Send`, `ReceiveFrom`, `SendTo`y `Accept` (todas heredadas de `CAsyncSocket`), no devuelven un error de `WSAEWOULDBLOCK` en `CSocket`. En su lugar, estas funciones esperan hasta que se complete la operación. Además, la llamada original terminará con el error WSAEINTR si se llama a `CancelBlockingCall` mientras una de estas funciones está bloqueando.

Para usar un objeto de `CSocket`, llame al constructor y, a continuación, llame a `Create` para crear el identificador de SOCKET subyacente (tipo SOCKET). Los parámetros predeterminados de `Create` crear un socket de secuencia, pero si no está utilizando el socket con un objeto `CArchive`, puede especificar un parámetro para crear un socket de datagrama en su lugar o enlazar a un puerto específico para crear un socket de servidor. Conéctese a un socket de cliente mediante `Connect` en el lado cliente y `Accept` en el lado servidor. A continuación, cree un objeto `CSocketFile` y asócielo al objeto `CSocket` en el constructor `CSocketFile`. A continuación, cree un objeto de `CArchive` para enviar y otro para recibir datos (según sea necesario) y, a continuación, asócielos con el objeto `CSocketFile` en el constructor `CArchive`. Una vez completadas las comunicaciones, destruya los objetos `CArchive`, `CSocketFile`y `CSocket`. El tipo de datos SOCKET se describe en el artículo [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

Cuando se usa `CArchive` con `CSocketFile` y `CSocket`, es posible que se produzca una situación en la que `CSocket::Receive` entre en un bucle (`PumpMessages(FD_READ)`) que espera la cantidad de bytes solicitada. Esto se debe a que Windows Sockets solo permite una llamada recibida por FD_READ notificación, pero `CSocketFile` y `CSocket` permiten varias llamadas recibidas por FD_READ. Si obtiene una FD_READ cuando no hay datos para leer, la aplicación se bloquea. Si nunca obtiene otro FD_READ, la aplicación deja de comunicarse a través del socket.

Puede resolver este problema como se indica a continuación. En el método `OnReceive` de la clase Socket, llame a `CAsyncSocket::IOCtl(FIONREAD, ...)` antes de llamar al método `Serialize` de la clase de mensaje cuando los datos esperados que se van a leer del socket superan el tamaño de un paquete TCP (la unidad de transmisión máxima del medio de red, normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a que se reciban todos los datos y, a continuación, inicie la operación de lectura.

En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte del código.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Al utilizar sockets de MFC en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que use Sockets para inicializar las bibliotecas de Sockets. De forma predeterminada, solo se llama a `AfxSocketInit` en el subproceso principal.

Para obtener más información, vea [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: Cómo funcionan los sockets con archivos](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: secuencia de operaciones](../../mfc/windows-sockets-sequence-of-operations.md), Windows Sockets [: ejemplo de sockets que usan archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Requisitos

**Encabezado:** AfxSock. h

##  <a name="attach"></a>CSocket:: Attach

Llame a esta función miembro para adjuntar el identificador de `hSocket` a un objeto `CSocket`.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente.

### <a name="remarks"></a>Observaciones

El identificador de SOCKET se almacena en el miembro de datos [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) del objeto.

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket:: CancelBlockingCall

Llame a esta función miembro para cancelar una llamada de bloqueo actualmente en curso.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Observaciones

Esta función cancela cualquier operación de bloqueo pendiente para este socket. La llamada de bloqueo original finalizará lo antes posible con el error WSAEINTR.

En el caso de una operación de bloqueo `Connect`, la implementación de Windows Sockets finalizará la llamada de bloqueo lo antes posible, pero es posible que no sea posible que se liberen los recursos de socket hasta que la conexión se haya completado (y se haya restablecido) o haya agotado el tiempo de espera. Es probable que esto sea perceptible solo si la aplicación intenta abrir inmediatamente un nuevo socket (si no hay Sockets disponibles) o para conectarse al mismo nodo del mismo nivel.

La cancelación de cualquier operación que no sea `Accept` puede dejar el socket en un estado indeterminado. Si una aplicación cancela una operación de bloqueo en un socket, la única operación que la aplicación puede depender de poder realizar en el socket es una llamada a `Close`, aunque otras operaciones pueden funcionar en algunas implementaciones de Windows Sockets. Si desea obtener la máxima portabilidad de la aplicación, debe tener cuidado de no depender de la realización de operaciones después de una cancelación.

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>CSocket:: Create

Llame a la función miembro **Create** después de construir un objeto socket para crear el socket de Windows y adjuntarlo.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
Un puerto concreto que se va a utilizar con el socket, o 0 si desea que MFC Seleccione un puerto.

*nSocketType*<br/>
SOCK_STREAM o SOCK_DGRAM.

*lpszSocketAddress*<br/>
Un puntero a una cadena que contiene la dirección de red del socket conectado, un número de puntos como "128.56.22.8". Al pasar la cadena NULL para este parámetro, se indica que la instancia de `CSocket` debe escuchar la actividad del cliente en todas las interfaces de red.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realiza correctamente; de lo contrario, es 0 y un código de error específico se puede recuperar llamando a `GetLastError`.

### <a name="remarks"></a>Observaciones

`Create` llama a `Bind` para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:

- SOCK_STREAM proporciona secuencias de bytes secuenciadas, confiables y bidireccionales basadas en conexión. Usa el protocolo de control de transmisión (TCP) para la familia de direcciones de Internet.

- SOCK_DGRAM admite datagramas, que son búferes sin conexión y no confiables de una longitud máxima fija (normalmente pequeña). Usa el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet. Para usar esta opción, no debe utilizar el socket con un objeto `CArchive`.

    > [!NOTE]
    >  La función miembro `Accept` toma una referencia a un nuevo objeto `CSocket` vacío como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Tenga en cuenta que si este objeto de socket sale del ámbito, la conexión se cierra. No llame a `Create` para este nuevo objeto de socket.

Para obtener más información sobre los sockets de flujo y de datagramas, vea los artículos [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: puertos y direcciones de socket](../../mfc/windows-sockets-ports-and-socket-addresses.md)y [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>CSocket:: CSocket

Construye un objeto `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Observaciones

Después de la construcción, debe llamar a la función miembro `Create`.

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>CSocket:: FromHandle

Devuelve un puntero a un objeto `CSocket`.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto `CSocket`, o NULL si no hay ningún objeto `CSocket` asociado a *hSocket*.

### <a name="remarks"></a>Observaciones

Cuando se proporciona un identificador de SOCKET, si un objeto de `CSocket` no está asociado al identificador, la función miembro devuelve NULL y no crea un objeto temporal.

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>CSocket:: IsBlocking

Llame a esta función miembro para determinar si una llamada de bloqueo está en curso.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el socket está bloqueando; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>CSocket:: OnMessagePending

Invalide esta función miembro para buscar mensajes determinados de Windows y responder a ellos en el socket.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha controlado el mensaje; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Se trata de un reemplazable avanzado.

El marco de trabajo llama a `OnMessagePending` mientras el socket está bombeando mensajes de Windows para ofrecerle la oportunidad de tratar los mensajes de interés para la aplicación. Para obtener ejemplos de cómo puede usar `OnMessagePending`, vea el artículo [Windows Sockets: derivar de clases de socket](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Consulte también

[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
