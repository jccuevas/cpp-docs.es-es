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
ms.openlocfilehash: 3f0a7a9a90250ede7b112cfbd9bc1ca14d583356
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318190"
---
# <a name="csocket-class"></a>CSocket (clase)

Deriva de `CAsyncSocket`, hereda su encapsulación de la API de Windows Sockets y representa `CAsyncSocket` un nivel de abstracción más alto que el de un objeto.

## <a name="syntax"></a>Sintaxis

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Construye un objeto `CSocket`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSocket::Attach](#attach)|Asocia un identificador SOCKET `CSocket` a un objeto.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Cancela una llamada de bloqueo que está actualmente en curso.|
|[CSocket::Crear](#create)|Crea un socket.|
|[CSocket::FromHandle](#fromhandle)|Devuelve un puntero `CSocket` a un objeto, dado un identificador SOCKET.|
|[CSocket::IsBlocking](#isblocking)|Determina si una llamada de bloqueo está en curso.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Se llama para procesar los mensajes pendientes mientras espera a que se complete una llamada de bloqueo.|

## <a name="remarks"></a>Observaciones

`CSocket`trabaja con `CSocketFile` `CArchive` clases y para gestionar el envío y recepción de datos.

Un `CSocket` objeto también proporciona bloqueo, que es `CArchive`esencial para el funcionamiento sincrónico de . Las funciones `Receive`de `Send` `ReceiveFrom`bloqueo, como , , `SendTo`, , y `Accept` (todas heredadas de `CAsyncSocket`), no devuelven un `WSAEWOULDBLOCK` error en `CSocket`. En su lugar, estas funciones esperan hasta que se complete la operación. Además, la llamada original terminará con el error `CancelBlockingCall` WSAEINTR si se llama mientras que una de estas funciones está bloqueando.

Para usar `CSocket` un objeto, llame `Create` al constructor y, a continuación, llame para crear el identificador SOCKET subyacente (tipo SOCKET). Los parámetros `Create` predeterminados de crear un socket de secuencia, pero si no está utilizando el socket con un `CArchive` objeto, puede especificar un parámetro para crear un socket de datagrama en su lugar, o enlazar a un puerto específico para crear un socket de servidor. Conéctese a un `Connect` socket de `Accept` cliente mediante en el lado del cliente y en el lado del servidor. A continuación, cree un `CSocketFile` `CSocket` objeto y `CSocketFile` asócielo al objeto en el constructor. A continuación, `CArchive` cree un objeto para enviar y otro para `CSocketFile` recibir datos `CArchive` (según sea necesario) y, a continuación, asócielos con el objeto en el constructor. Cuando se completen `CArchive`las `CSocketFile`comunicaciones, destruya los objetos , , y `CSocket` . El tipo de datos SOCKET se describe en el artículo [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

Cuando usted `CArchive` `CSocketFile` utiliza `CSocket`con y , `CSocket::Receive` usted puede ser `PumpMessages(FD_READ)`que encuentre una situación donde entra un loop (por ) esperando la cantidad solicitada de bytes. Esto se debe a que los sockets de `CSocketFile` Windows `CSocket` solo permiten una llamada recv por notificación FD_READ, pero y permiten varias llamadas recv por FD_READ. Si obtiene una FD_READ cuando no hay datos que leer, la aplicación se bloquea. Si nunca obtiene otro FD_READ, la aplicación deja de comunicarse a través del socket.

Puede resolver este problema de la siguiente manera. En `OnReceive` el método de la `CAsyncSocket::IOCtl(FIONREAD, ...)` clase de `Serialize` socket, llame antes de llamar al método de la clase de mensaje cuando los datos esperados que se leerán desde el socket superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red, normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a que se reciban todos los datos y, a continuación, inicie la operación de lectura.

En el ejemplo `m_dwExpected` siguiente, es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte del código.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> Al usar sockets MFC en subprocesos secundarios en una `AfxSocketInit` aplicación MFC vinculada estáticamente, debe llamar a cada subproceso que usa sockets para inicializar las bibliotecas de sockets. De forma `AfxSocketInit` predeterminada, solo se llama en el subproceso principal.

Para obtener más información, vea [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), Windows [Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: How Sockets with Archives Work](../../mfc/windows-sockets-how-sockets-with-archives-work.md), Windows [Sockets: Sequence of Operations](../../mfc/windows-sockets-sequence-of-operations.md), Windows [Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>CSocket::Attach

Llame a esta función miembro para asociar el `hSocket` identificador a un `CSocket` objeto.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente.

### <a name="remarks"></a>Observaciones

El identificador SOCKET se almacena en el miembro de datos [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) del objeto.

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>CSocket::CancelBlockingCall

Llame a esta función miembro para cancelar una llamada de bloqueo actualmente en curso.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Observaciones

Esta función cancela cualquier operación de bloqueo pendiente para este socket. La llamada de bloqueo original terminará tan pronto como sea posible con el error WSAEINTR.

En el caso `Connect` de una operación de bloqueo, la implementación de Windows Sockets finalizará la llamada de bloqueo tan pronto como sea posible, pero es posible que no sea posible que los recursos de socket se liberen hasta que la conexión se haya completado (y luego se haya restablecido) o se haya agotado el tiempo de espera. Esto es probable que sea notable sólo si la aplicación intenta abrir inmediatamente un nuevo socket (si no hay sockets disponibles), o para conectarse al mismo par.

Cancelar cualquier operación `Accept` que no sea puede dejar el socket en un estado indeterminado. Si una aplicación cancela una operación de bloqueo en un socket, la única operación que `Close`la aplicación puede depender de poder realizar en el socket es una llamada a , aunque otras operaciones pueden funcionar en algunas implementaciones de Windows Sockets. Si desea la máxima portabilidad de la aplicación, debe tener cuidado de no depender de la realización de operaciones después de una cancelación.

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcreate"></a><a name="create"></a>CSocket::Crear

Llame a la **create** función miembro después de construir un objeto de socket para crear el socket de Windows y adjuntarlo.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parámetros

*nSocketPort*<br/>
Un puerto determinado que se usará con el socket, o 0 si desea que MFC seleccione un puerto.

*nSocketType*<br/>
SOCK_STREAM o SOCK_DGRAM.

*lpszSocketAddress*<br/>
Un puntero a una cadena que contiene la dirección de red del socket conectado, un número punteado como "128.56.22.8". Pasar la cadena NULL para `CSocket` este parámetro indica que la instancia debe escuchar la actividad del cliente en todas las interfaces de red.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función es correcta; de lo contrario 0, y un código `GetLastError`de error específico se puede recuperar llamando a .

### <a name="remarks"></a>Observaciones

`Create`a `Bind` continuación, llama para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:

- SOCK_STREAM Proporciona secuencias de bytes secuenciadas, fiables, bidireccionales y basadas en conexiones. Utiliza el protocolo de control de transmisión (TCP) para la familia de direcciones de Internet.

- SOCK_DGRAM Admite datagramas, que son búferes sin conexión y poco fiables de una longitud máxima fija (normalmente pequeña). Utiliza el Protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet. Para utilizar esta opción, no debe `CArchive` utilizar el socket con un objeto.

    > [!NOTE]
    >  La `Accept` función miembro toma una `CSocket` referencia a un nuevo objeto vacío como parámetro. Debe construir este objeto `Accept`antes de llamar a . Tenga en cuenta que si este objeto de socket sale del ámbito, la conexión se cierra. No llame `Create` a este nuevo objeto de socket.

Para obtener más información acerca de los sockets de flujo y datagramas, vea los artículos [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md)y Windows [Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcsocket"></a><a name="csocket"></a>CSocket::CSocket

Construye un objeto `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Observaciones

Después de la `Create` construcción, debe llamar a la función miembro.

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>CSocket::FromHandle

Devuelve un puntero `CSocket` a un objeto.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parámetros

*hSocket*<br/>
Contiene un identificador de un socket.

### <a name="return-value"></a>Valor devuelto

Un puntero `CSocket` a un objeto, o `CSocket` NULL si no hay ningún objeto asociado a *hSocket*.

### <a name="remarks"></a>Observaciones

Cuando se le da `CSocket` un identificador SOCKET, si un objeto no está asociado al identificador, la función miembro devuelve NULL y no crea un objeto temporal.

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketisblocking"></a><a name="isblocking"></a>CSocket::IsBlocking

Llame a esta función miembro para determinar si una llamada de bloqueo está en curso.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el socket está bloqueando; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>CSocket::OnMessagePending

Invalide esta función miembro para buscar mensajes concretos de Windows y responder a ellos en el socket.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controló el mensaje; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este es un avanzado reemplazable.

El marco `OnMessagePending` de trabajo llama mientras el socket está bombeando mensajes de Windows para darle la oportunidad de tratar con mensajes de interés para la aplicación. Para obtener ejemplos de `OnMessagePending`cómo puede usar , vea el artículo [Windows Sockets: De riving from Socket Classes](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Consulte también

[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
