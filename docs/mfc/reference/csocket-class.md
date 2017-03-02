---
title: CSocket (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocket
dev_langs:
- C++
helpviewer_keywords:
- WinSock CSocket class
- CSocket class
- SOCKET handle
- sockets classes
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: 30
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 451ea100dbf02e365204fe4fdf1c380e855d8231
ms.lasthandoff: 02/24/2017

---
# <a name="csocket-class"></a>CSocket (clase)
Se deriva de `CAsyncSocket`, hereda su encapsulación de la API Windows Sockets y representa un nivel de abstracción superior que el de un `CAsyncSocket` objeto.  
  
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
|[CSocket::Attach](#attach)|Asocia un **SOCKET** identificador de un `CSocket` objeto.|  
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Cancela una llamada de bloqueo que está actualmente en curso.|  
|[CSocket::Create](#create)|Crea un socket.|  
|[CSocket::FromHandle](#fromhandle)|Devuelve un puntero a un `CSocket` objeto, dado un **SOCKET** controlar.|  
|[CSocket::IsBlocking](#isblocking)|Determina si una llamada de bloqueo está en curso.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Múltiple](#onmessagepending)|Se llama para procesar los mensajes pendientes mientras se espera a que se complete una llamada de bloqueo.|  
  
## <a name="remarks"></a>Comentarios  
 `CSocket`funciona con las clases `CSocketFile` y `CArchive` para administrar el envío y recepción de datos.  
  
 Un `CSocket` objeto también proporciona bloqueo, que es esencial para el funcionamiento sincrónico de `CArchive`. Bloqueo de las funciones, como `Receive`, `Send`, `ReceiveFrom`, `SendTo`, y `Accept` (todos los heredados de `CAsyncSocket`), no devuelven un `WSAEWOULDBLOCK` error en `CSocket`. En su lugar, estas funciones espere hasta que se complete la operación. Además, la llamada original se cerrará con el error `WSAEINTR` si `CancelBlockingCall` llama mientras se está bloqueando una de estas funciones.  
  
 Utilizar un `CSocket` objeto, llame al constructor, a continuación, llame a `Create` para crear la base de `SOCKET` controlar (tipo `SOCKET`). Los parámetros predeterminados de `Create` crear un socket de secuencia, pero si no está utilizando el socket con un `CArchive` objeto, puede especificar un parámetro para crear un socket de datagrama en su lugar, ni enlazarse a un puerto específico para crear un socket de servidor. Conectar con un socket de cliente mediante `Connect` en el cliente y `Accept` en el servidor. A continuación, cree una `CSocketFile` objeto y asociarla a la `CSocket` objeto en el `CSocketFile` constructor. A continuación, cree una `CArchive` objeto para el envío y otro para recibir datos (según sea necesario), a continuación, asociar con la `CSocketFile` objeto en el `CArchive` constructor. Cuando se completan las comunicaciones, destruir el `CArchive`, `CSocketFile`, y `CSocket` objetos. El `SOCKET` tipo de datos se describe en el artículo [Windows Sockets: fondo](../../mfc/windows-sockets-background.md).  
  
 Al usar `CArchive` con `CSocketFile` y `CSocket`, puede darse el caso donde `CSocket::Receive` entra en un bucle (mediante `PumpMessages(FD_READ)`) esperando la cantidad de bytes solicitada. Esto es porque Windows sockets permite sólo una llamada recibidas por notificación FD_READ, pero `CSocketFile` y `CSocket` permiten varias llamadas recibidas por FD_READ. Si obtiene un FD_READ cuando no hay ningún dato que leer, se bloquea la aplicación. Si no aparece otro FD_READ nunca, la aplicación deja de comunicarse a través del socket.  
  
 Puede resolver este problema como sigue. En el `OnReceive` método de la clase socket, llamada `CAsyncSocket::IOCtl(FIONREAD, ...)` antes de llamar a la `Serialize` método de la clase de mensaje cuando los datos esperados para el socket deba leer superan el tamaño de un paquete TCP (unidad de transmisión máxima del medio de red, normalmente al menos 1096 bytes). Si el tamaño de los datos disponibles es menor que el necesario, esperar todos los datos recibir y luego iniciar la operación de lectura.  
  
 En el ejemplo siguiente, `m_dwExpected` es el número aproximado de bytes que el usuario espera recibir. Se supone que se declara en otra parte del código.  
  
 [!code-cpp[NVC_MFCSocketThread Nº&4;](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]  
  
> [!NOTE]
>  Al utilizar sockets MFC en subprocesos secundarios en una aplicación MFC vinculado estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se llama sólo en el subproceso principal.  
  
 Para obtener más información, consulte [Windows Sockets en MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: funcionamiento de los Sockets con archivos de trabajo](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: orden de operaciones](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: ejemplo de Sockets con archivos](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsock.h  
  
##  <a name="a-nameattacha--csocketattach"></a><a name="attach"></a>CSocket::Attach  
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
 [!code-cpp[1 NVC_MFCSocketThread](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]  
  
 [!code-cpp[NVC_MFCSocketThread&#2;](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCSocketThread&3;](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]  
  
##  <a name="a-namecancelblockingcalla--csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>CSocket::CancelBlockingCall  
 Llame a esta función miembro para cancelar una llamada de bloqueo actualmente en curso.  
  
```  
void CancelBlockingCall();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función cancela cualquier operación de bloqueo pendiente para este socket. La llamada de bloqueo original se terminará tan pronto como sea posible con el error **WSAEINTR**.  
  
 En el caso de un bloqueo **conectar** , la implementación de Windows Sockets finalizará la operación la llamada de bloqueo tan pronto como sea posible, pero puede no ser posible para los recursos de socket que se libere hasta que la conexión ha completado (y, a continuación, se ha restablecido) o tiempo de espera. Esto es probable que sean evidentes sólo si la aplicación intenta inmediatamente para abrir un nuevo socket (si no hay sockets disponibles), o para conectar con el mismo nivel.  
  
 Cancelar cualquier operación que no sea **Accept** puede dejar el socket en un estado indeterminado. Si una aplicación cancela una operación en un socket de bloqueo, la única operación que puede depender de la aplicación que se va a llevar a cabo en el socket es una llamada a **cerrar**, aunque otras operaciones pueden funcionar en algunas implementaciones de Windows Sockets. Si desea máxima portabilidad para su aplicación, debe ser cuidado de no dependen de realizar operaciones después de la cancelación.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="a-namecreatea--csocketcreate"></a><a name="create"></a>CSocket::Create  
 Llame a la **crear** función miembro después de crear un objeto de socket para crear el socket de Windows y adjuntarlo.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSocketPort`  
 Un puerto determinado para usarse con el socket, o 0 si desea que MFC para seleccionar un puerto.  
  
 `nSocketType`  
 **SOCK_STREAM** o **SOCK_DGRAM**.  
  
 `lpszSocketAddress`  
 Un puntero a una cadena que contiene la dirección de red del socket conectado, un número de puntos, como "128.56.22.8". Pasar el **NULL** la cadena de este parámetro indica la **CSocket** instancia debe escuchar la actividad del cliente en todas las interfaces de red.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 y un código de error específico se pueden recuperar mediante una llamada a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** , a continuación, se llama **enlace** para enlazar el socket a la dirección especificada. Se admiten los siguientes tipos de socket:  
  
- **SOCK_STREAM** proporciona secuenciado, secuencias de bytes bidireccionales confiables, basadas en conexión,. Utiliza el protocolo de Control de transmisión (TCP) para la familia de direcciones de Internet.  
  
- **SOCK_DGRAM** admite datagramas, que son búferes sin conexión y no confiables de longitud máxima fija (normalmente corta). Utiliza el protocolo de datagramas de usuario (UDP) para la familia de direcciones de Internet. Para usar esta opción, no debe utilizar el socket con un `CArchive` objeto.  
  
    > [!NOTE]
    >  El **Accept** función miembro toma una referencia a un nuevo `CSocket` objeto como su parámetro. Debe construir este objeto antes de llamar a **Accept**. Tenga en cuenta que si este objeto socket se sale del ámbito, se cerrará la conexión. No llame a **crear** para este nuevo objeto de socket.  
  
 Para obtener más información acerca de los sockets de secuencia y datagrama, consulte los artículos [Windows Sockets: fondo](../../mfc/windows-sockets-background.md), [Windows Sockets: puertos y direcciones de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md), y [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="a-namecsocketa--csocketcsocket"></a><a name="csocket"></a>CSocket::CSocket  
 Construye un objeto `CSocket`.  
  
```  
CSocket();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de la construcción, se debe llamar a la **crear** función miembro.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="a-namefromhandlea--csocketfromhandle"></a><a name="fromhandle"></a>CSocket::FromHandle  
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
 Cuando se da una **SOCKET** controlar si una `CSocket` objeto no está asociado al identificador, la función miembro devuelve **NULL** y no crea un objeto temporal.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="a-nameisblockinga--csocketisblocking"></a><a name="isblocking"></a>CSocket::IsBlocking  
 Llame a esta función miembro para determinar si una llamada de bloqueo está en curso.  
  
```  
BOOL IsBlocking();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se está bloqueando el socket; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="a-nameonmessagependinga--csocketonmessagepending"></a><a name="onmessagepending"></a>Múltiple  
 Reemplace esta función miembro para buscar mensajes concretos de Windows y responder a ellas en el socket.  
  
```  
virtual BOOL OnMessagePending();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el mensaje; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Avanzada reemplazable.  
  
 El marco llama `OnMessagePending` mientras el socket suministra mensajes de Windows para proporcionar una oportunidad para tratar con mensajes de interés para la aplicación. Para obtener ejemplos de cómo puede usar `OnMessagePending`, vea el artículo [Windows Sockets: derivar desde clases de Socket](../../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="see-also"></a>Vea también  
 [CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket (clase)](../../mfc/reference/casyncsocket-class.md)   
 [Clase CSocketFile](../../mfc/reference/csocketfile-class.md)

