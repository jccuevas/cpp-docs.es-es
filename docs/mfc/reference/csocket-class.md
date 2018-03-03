---
title: CSocket (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ae8a30697783b478e9ffdb1c247f52d7b9f2ac2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="csocket-class"></a>CSocket (clase)
Se deriva de `CAsyncSocket`, hereda su encapsulación de la API de Windows Sockets y representa un mayor nivel de abstracción que el de un `CAsyncSocket` objeto.  
  
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
|[CSocket::Attach](#attach)|Asocia un **SOCKET** identificador de un `CSocket` objeto.|  
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Cancela una llamada de bloqueo que está actualmente en curso.|  
|[CSocket::Create](#create)|Crea un socket.|  
|[CSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CSocket` objeto, dado un **SOCKET** controlar.|  
|[CSocket::IsBlocking](#isblocking)|Determina si una llamada de bloqueo está en curso.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Múltiple](#onmessagepending)|Se llama para procesar mensajes pendientes mientras se espera a que se complete una llamada de bloqueo.|  
  
## <a name="remarks"></a>Comentarios  
 `CSocket`funciona con las clases `CSocketFile` y `CArchive` para administrar el envío y recepción de datos.  
  
 A `CSocket` objeto también proporciona bloqueo, que es esencial para el funcionamiento sincrónico de `CArchive`. Bloqueo de las funciones, como `Receive`, `Send`, `ReceiveFrom`, `SendTo`, y `Accept` (todos los heredados de `CAsyncSocket`), no devuelven un `WSAEWOULDBLOCK` error en `CSocket`. En su lugar, estas funciones esperan hasta que se complete la operación. Además, la llamada original se cerrará con el error `WSAEINTR` si `CancelBlockingCall` se llama mientras está bloqueando la una de estas funciones.  
  
 Para usar un `CSocket` de objeto, llame al constructor, a continuación, llame a `Create` crear subyacente `SOCKET` controlar (tipo `SOCKET`). Los parámetros predeterminados de `Create` crear un socket de secuencia, sin embargo, si no está utilizando el socket con un `CArchive` objeto, puede especificar un parámetro para crear un socket de datagrama en su lugar, ni enlazarse a un puerto específico para crear un socket de servidor. Conectarse a un socket de cliente mediante `Connect` en el lado del cliente y `Accept` en el servidor. A continuación, cree un `CSocketFile` objeto y asociarlo a la `CSocket` objeto en el `CSocketFile` constructor. A continuación, cree un `CArchive` objeto para el envío y otro para recibir datos (según sea necesario), a continuación, asociar con la `CSocketFile` objeto en el `CArchive` constructor. Cuando finalizan las comunicaciones, destruir la `CArchive`, `CSocketFile`, y `CSocket` objetos. El `SOCKET` tipo de datos se describe en el artículo [Windows Sockets: fondo](../../mfc/windows-sockets-background.md).  
  
 Cuando usas `CArchive` con `CSocketFile` y `CSocket`, puede darse el caso donde `CSocket::Receive` entra en un bucle (por `PumpMessages(FD_READ)`) esperando la cantidad de bytes solicitada. Esto es porque Windows sockets permite sólo una llamada de recepción por la notificación de FD_READ, pero `CSocketFile` y `CSocket` permitir varias llamadas de recepción por FD_READ. Si recibe un FD_READ cuando no hay datos para leer, la aplicación se bloquea. Si nunca se produce otro FD_READ, la aplicación deja de comunicarse a través del socket.  
  
 Puede resolver este problema como se indica a continuación. En el `OnReceive` método de la clase socket, llamada `CAsyncSocket::IOCtl(FIONREAD, ...)` antes de llamar a la `Serialize` método de la clase de mensaje cuando los datos esperados para leer desde el socket superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, espere a todos los datos que puede recibir y luego iniciar la operación de lectura.  
  
 En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte en el código.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]  
  
> [!NOTE]
>  Al utilizar sockets de MFC en subprocesos secundarios en una aplicación MFC vinculado estáticamente, se debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se denomina solo en el subproceso principal.  
  
 Para obtener más información, consulte [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: funcionamiento de los Sockets con archivos de trabajo](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: secuencia de operaciones](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: ejemplo de Sockets que usan archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsock.h  
  
##  <a name="attach"></a>CSocket::Attach  
 Llame a esta función miembro para adjuntar el `hSocket` identificador de un `CSocket` objeto.  
  
```  
BOOL Attach(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parámetros  
 `hSocket`  
 Contiene un identificador de un socket.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 El **SOCKET** identificador se almacena en el objeto [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) miembro de datos.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]  
  
 [!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]  
  
##  <a name="cancelblockingcall"></a>CSocket::CancelBlockingCall  
 Llame a esta función miembro para cancelar una llamada de bloqueo actualmente en curso.  
  
```  
void CancelBlockingCall();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función cancela cualquier operación de bloqueo pendiente para este socket. La llamada bloqueo original se terminará tan pronto como sea posible con el error **WSAEINTR**.  
  
 En el caso de un bloqueo **conectar** , la implementación de Windows Sockets finalizará la operación la llamada de bloqueo tan pronto como sea posible, pero puede no ser posible para los recursos de socket que se libere hasta que haya finalizado la conexión (y, a continuación, se ha restablecido) o tiempo de espera. Esto es probable que sea importante solo si la aplicación intenta inmediatamente para abrir un nuevo socket (si no hay sockets disponibles), o para conectar con el mismo nodo.  
  
 Cancelar cualquier operación distinta de **Accept** puede dejar el socket en un estado indeterminado. Si una aplicación cancela una operación de bloqueo en un socket, la única operación que puede depender de la aplicación que se va a llevar a cabo en el socket es una llamada a **cerrar**, aunque otras operaciones pueden funcionar en algunos Windows Sockets implementaciones. Si desea la máxima portabilidad de la aplicación, debe ser cuidado de no dependen de realizar operaciones después de una cancelación.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="create"></a>CSocket::Create  
 Llame a la **crear** función miembro después de crear un objeto de socket para crear el socket de Windows y adjúntela.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSocketPort`  
 Un puerto determinado para su uso con el socket, o 0 si desea que MFC para seleccionar un puerto.  
  
 `nSocketType`  
 **SOCK_STREAM** o **SOCK_DGRAM**.  
  
 `lpszSocketAddress`  
 Un puntero a una cadena que contiene la dirección de red del socket conectado, un número separado por puntos, como "128.56.22.8". Pasar el **NULL** de cadena para este parámetro indica la **CSocket** instancia debe escuchar la actividad del cliente en todas las interfaces de red.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** , a continuación, se llama **enlazar** para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:  
  
- **SOCK_STREAM** proporciona secuenciado, secuencias de bytes bidireccional, confiable y basada en la conexión. Usa el protocolo de Control de transmisión (TCP) para la familia de direcciones de Internet.  
  
- **SOCK_DGRAM** admite datagramas, que son búferes sin conexión y no confiables de longitud máxima fija (normalmente corta). Usa el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet. Para usar esta opción, no debe utilizar el socket con un `CArchive` objeto.  
  
    > [!NOTE]
    >  El **Accept** función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Se debe crear este objeto antes de llamar a **Accept**. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. No llame a **crear** para este nuevo objeto de socket.  
  
 Para obtener más información acerca de los sockets de secuencia y datagrama, vea los artículos [Windows Sockets: fondo](../../mfc/windows-sockets-background.md), [Windows Sockets: puertos y direcciones de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md), y [Windows Sockets: usar Los sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="csocket"></a>CSocket::CSocket  
 Construye un objeto `CSocket`.  
  
```  
CSocket();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de la construcción, se debe llamar a la **crear** función miembro.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="fromhandle"></a>CSocket::FromHandle  
 Devuelve un puntero a un `CSocket` objeto.  
  
```  
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parámetros  
 `hSocket`  
 Contiene un identificador de un socket.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CSocket` objeto, o **NULL** si no hay ningún `CSocket` objeto asociado al `hSocket`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se especifica un **SOCKET** controlar si una `CSocket` objeto no está asociado al identificador, la función miembro devuelve **NULL** y no crea un objeto temporal.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="isblocking"></a>CSocket::IsBlocking  
 Llame a esta función miembro para determinar si una llamada de bloqueo está en curso.  
  
```  
BOOL IsBlocking();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se está bloqueando el socket; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="onmessagepending"></a>Múltiple  
 Reemplace esta función miembro para buscar mensajes concretos de Windows y responder a ellas en el socket.  
  
```  
virtual BOOL OnMessagePending();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el mensaje; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Avanzada reemplazable.  
  
 Las llamadas de framework `OnMessagePending` mientras el socket suministra mensajes de Windows para darle la oportunidad de tratar con mensajes de interés para la aplicación. Para obtener ejemplos de cómo puede usar `OnMessagePending`, vea el artículo [Windows Sockets: derivar desde clases de Socket](../../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="see-also"></a>Vea también  
 [CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
