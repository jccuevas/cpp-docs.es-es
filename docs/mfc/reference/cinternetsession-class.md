---
title: CInternetSession (clase)
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: c9b8eaf51820dfcd08c1390c8645978fa403931d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505842"
---
# <a name="cinternetsession-class"></a>CInternetSession (clase)

Crea e inicializa una o varias sesiones de Internet simultáneas y, si es necesario, describe la conexión a un servidor proxy.

## <a name="syntax"></a>Sintaxis

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Construye un objeto `CInternetSession`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInternetSession::Close](#close)|Cierra la conexión a Internet cuando finaliza la sesión de Internet.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Establece una rutina de devolución de llamada de estado.|
|[CInternetSession::GetContext](#getcontext)|Cierra la conexión a Internet cuando finaliza la sesión de Internet.|
|[CInternetSession::GetCookie](#getcookie)|Devuelve las cookies para la dirección URL especificada y todas sus direcciones URL primarias.|
|[CInternetSession::GetCookieLength](#getcookielength)|Recupera la variable que especifica la longitud de la cookie almacenada en el búfer.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Abre una sesión de FTP con un servidor. Inicia sesión en el usuario.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Abre un servidor gopher para una aplicación que está intentando abrir una conexión.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Abre un servidor HTTP para una aplicación que está intentando abrir una conexión.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Actualiza el estado de una operación cuando la devolución de llamada de estado está habilitada.|
|[CInternetSession::OpenURL](#openurl)|Analiza y abre una dirección URL.|
|[CInternetSession::SetCookie](#setcookie)|Establece una cookie para la dirección URL especificada.|
|[CInternetSession::SetOption](#setoption)|Establece las opciones de la sesión de Internet.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInternetSession:: Operator HINTERNET](#operator_hinternet)|Identificador de la sesión de Internet actual.|

## <a name="remarks"></a>Comentarios

Si se debe mantener la conexión a Internet mientras dure una aplicación, puede crear un `CInternetSession` miembro de la clase [CWinApp](../../mfc/reference/cwinapp-class.md).

Una vez establecida una sesión de Internet, puede llamar a [OpenURL](#openurl). `CInternetSession`después, analiza la dirección URL mediante una llamada a la función global [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Independientemente de su tipo de protocolo `CInternetSession` , interpreta la dirección URL y la administra automáticamente. Puede controlar las solicitudes de archivos locales identificados con el recurso de dirección URL "file://". `OpenURL`devolverá un puntero a un objeto [CStdioFile](../../mfc/reference/cstdiofile-class.md) si el nombre que se pasa es un archivo local.

Si abre una dirección URL en un servidor de Internet `OpenURL`con, puede leer información del sitio. Si desea realizar acciones específicas del servicio (por ejemplo, HTTP, FTP o Gopher) en archivos ubicados en un servidor, debe establecer la conexión adecuada con dicho servidor. Para abrir un determinado tipo de conexión directamente a un servicio determinado, utilice una de las siguientes funciones miembro:

- [GetGopherConnection](#getgopherconnection) para abrir una conexión a un servicio Gopher.

- [GetHttpConnection](#gethttpconnection) para abrir una conexión a un servicio http.

- [GetFtpConnection](#getftpconnection) para abrir una conexión a un servicio FTP.

[SetOption](#setoption) le permite establecer las opciones de consulta de su sesión, como los valores de tiempo de espera, el número de reintentos, etc.

`CInternetSession`las funciones miembro [setcookie](#setcookie), [GetCookie](#getcookie)y [GetCookieLength](#getcookielength) proporcionan los medios para administrar una base de datos de cookies Win32, a través de la cual los servidores y scripts mantienen información de estado sobre la estación de trabajo cliente.

Para obtener más información sobre las tareas básicas de programación de Internet [, vea el artículo pasos de Internet First: WinInet](../../mfc/wininet-basics.md). Para obtener información general sobre el uso de las clases WinInet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`producirá una [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) para los tipos de servicio no compatibles. Actualmente solo se admiten los siguientes tipos de servicio: FTP, HTTP, gopher y archivo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

Se llama a esta función miembro cuando `CInternetSession` se crea un objeto.

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*pstrAgent*<br/>
Puntero a una cadena que identifica el nombre de la aplicación o entidad que llama a las funciones de Internet (por ejemplo, "explorador de Internet de Microsoft"). Si *pstrAgent* es null (valor predeterminado), el marco de trabajo llama a la función global [AfxGetAppName](application-information-and-management.md#afxgetappname), que devuelve una cadena terminada en null que contiene el nombre de una aplicación. Algunos protocolos usan esta cadena para identificar la aplicación en el servidor.

*dwContext*<br/>
Identificador de contexto para la operación. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](#onstatuscallback). El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que tenga se asociarán a ese identificador de contexto.

*dwAccessType*<br/>
Tipo de acceso necesario. Estos son los valores válidos, exactamente uno de los cuales se puede proporcionar:

- INTERNET_OPEN_TYPE_PRECONFIG Conéctese con la configuración preconfigurada en el registro. Este tipo de acceso se establece como el valor predeterminado. Para conectarse a través de un proxy TIS, establezca *dwAccessType* en este valor. después, establezca el registro correctamente.

- INTERNET_OPEN_TYPE_DIRECT Conéctese directamente a Internet.

- INTERNET_OPEN_TYPE_PROXY Conéctese a través de un proxy CERN.

Para obtener información acerca de cómo conectarse con distintos tipos de servidores proxy, consulte [los pasos de una aplicación cliente FTP típica](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Nombre del proxy de CERN preferido si *dwAccessType* está establecido como INTERNET_OPEN_TYPE_PROXY. El valor predeterminado es NULL.

*pstrProxyBypass*<br/>
Un puntero a una cadena que contiene una lista opcional de direcciones de servidor. Estas direcciones se pueden omitir cuando se usa el acceso proxy. Si se proporciona un valor NULL, la lista de omisión se leerá desde el registro. Este parámetro solo es significativo si *dwAccessType* está establecido en INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Indica varias opciones de almacenamiento en caché. El valor predeterminado se establece en 0. Los valores posibles son:

- INTERNET_FLAG_DONT_CACHE no almacenan en caché los datos, ya sea de forma local o en cualquier servidor de puerta de enlace.

- Las operaciones de descarga de INTERNET_FLAG_OFFLINE solo se satisfacen a través de la caché persistente. Si el elemento no existe en la memoria caché, se devuelve un código de error adecuado. Esta marca se puede combinar con el operador bit a **&#124;** bit or ().

### <a name="remarks"></a>Comentarios

`CInternetSession`es la primera función de Internet a la que llama una aplicación. Inicializa las estructuras de datos internas y se prepara para futuras llamadas desde la aplicación.

Si no se puede abrir una conexión a `CInternetSession` Internet, produce una [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>  CInternetSession::Close

Llame a esta función miembro cuando la aplicación haya terminado de `CInternetSession` usar el objeto.

```cpp
virtual void Close();
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

Llame a esta función miembro para habilitar la devolución de llamada de estado.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
Especifica si la devolución de llamada está habilitada o deshabilitada. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

### <a name="remarks"></a>Comentarios

Al controlar la devolución de llamada de estado, puede proporcionar el estado sobre el progreso de la operación (como resolver el nombre, conectarse al servidor, etc.) en la barra de estado de la aplicación. Mostrar el estado de la operación es especialmente conveniente durante una operación a largo plazo.

Dado que las devoluciones de llamada se producen durante el procesamiento de la solicitud, la aplicación debe invertir el menor tiempo posible en la devolución de llamada para evitar la degradación del rendimiento de los datos en la red. Por ejemplo, la colocación de un cuadro de diálogo en una devolución de llamada puede ser una operación tan larga que el servidor finaliza la solicitud.

No se puede quitar la devolución de llamada de estado mientras estén pendientes las devoluciones de llamada.

Para controlar las operaciones de forma asincrónica, debe crear su propio subproceso o usar las funciones WinInet sin MFC.

## <a name="getcontext"></a>  CInternetSession::GetContext

Llame a esta función miembro para obtener el valor de contexto para una sesión de aplicación determinada.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de contexto definido por la aplicación.

### <a name="remarks"></a>Comentarios

[OnStatusCallback](#onstatuscallback) usa el ID. de contexto `GetContext` devuelto por para informar del estado de una aplicación determinada. Por ejemplo, cuando un usuario activa una solicitud de Internet que implica devolver información de estado, la devolución de llamada de estado usa el ID. de contexto para notificar el estado de esa solicitud concreta. Si el usuario activa dos solicitudes de Internet independientes que implican la devolución de información `OnStatusCallback` de estado, usa los identificadores de contexto para devolver el estado de sus solicitudes correspondientes. Por lo tanto, el identificador de contexto se utiliza para todas las operaciones de devolución de llamada de estado y se asocia a la sesión hasta que finalice la sesión.

Para obtener más información acerca de las operaciones asincrónicas, [vea el artículo pasos de Internet First: WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>  CInternetSession::GetCookie

Esta función miembro implementa el comportamiento de la función [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)de Win32, como se describe en el Windows SDK.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Puntero a una cadena que contiene la dirección URL.

*pstrCookieName*<br/>
Puntero a una cadena que contiene el nombre de la cookie que se va a obtener para la dirección URL especificada.

*pstrCookieData*<br/>
En la primera sobrecarga, puntero a una cadena que contiene la dirección del búfer que recibe los datos de la cookie. Este valor puede ser NULL. En la segunda sobrecarga, una referencia a un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) para recibir los datos de la cookie.

*dwBufLen*<br/>
Variable que especifica el tamaño del búfer de *pstrCookieData* . Si la función se ejecuta correctamente, el búfer recibe la cantidad de datos copiados en el búfer de *pstrCookieData* . Si *pstrCookieData* es null, este parámetro recibe un valor que especifica el tamaño del búfer necesario para copiar todos los datos de cookies.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, o FALSE en caso contrario. Si se produce un error en la llamada, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error. Se aplican los siguientes valores de error:

- ERROR_NO_MORE_ITEMS no hay cookies para la dirección URL especificada y para todos sus elementos primarios.

- ERROR_INSUFFICIENT_BUFFER el valor pasado en *dwBufLen* es insuficiente para copiar todos los datos de cookies. El valor devuelto en *dwBufLen* es el tamaño del búfer necesario para obtener todos los datos.

### <a name="remarks"></a>Comentarios

En la segunda sobrecarga, MFC recupera los datos de la cookie en el `CString` objeto proporcionado.

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

Llame a esta función miembro para obtener la longitud de la cookie almacenada en el búfer.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Puntero a una cadena que contiene la dirección URL.

*pstrCookieName*<br/>
Puntero a una cadena que contiene el nombre de la cookie.

### <a name="return-value"></a>Valor devuelto

Valor DWORD que indica la longitud de la cookie, almacenada en el búfer. Cero si no existe ninguna cookie con el nombre indicado por *pstrCookieName* .

### <a name="remarks"></a>Comentarios

[GetCookie](#getcookie)usa este valor.

## <a name="getftpconnection"></a>  CInternetSession::GetFtpConnection

Llame a esta función miembro para establecer una conexión FTP y obtener un puntero a `CFtpConnection` un objeto.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parámetros

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor FTP.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario en el que se va a iniciar sesión. Si es NULL, el valor predeterminado es Anonymous.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se va a usar para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es null (o una cadena vacía), pero *PSTRUSERNAME* no es null, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de los cuatro valores posibles de *pstrUserName* y *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Nombre de usuario enviado al servidor FTP | Contraseña enviada al servidor FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL o ""   |   NULL o ""   |         Anonymous         |      Nombre de correo electrónico del usuario      |
| Cadena que no es NULL |   NULL o ""   |       *pstrUserName*        |             " "             |
|      NULL       | Cadena que no es NULL |            ERROR            |            ERROR            |
| Cadena que no es NULL | Cadena que no es NULL |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

*bPassive*<br/>
Especifica el modo pasivo o activo para esta sesión FTP. Si se establece en true, la API `dwFlag` Win32 se establece en INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CFtpConnection](../../mfc/reference/cftpconnection-class.md) . Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

### <a name="remarks"></a>Comentarios

`GetFtpConnection`se conecta a un servidor FTP y crea y devuelve un puntero a un `CFTPConnection` objeto. No realiza ninguna operación específica en el servidor. Si piensa leer o escribir en archivos, por ejemplo, debe realizar dichas operaciones como pasos independientes. Vea las clases [CFtpConnection](../../mfc/reference/cftpconnection-class.md) y [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) para obtener información sobre cómo buscar archivos, abrir archivos y leer o escribir en archivos. Vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos para realizar tareas comunes de conexión FTP.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

Llame a esta función miembro para establecer una nueva conexión gopher y obtener un puntero a `CGopherConnection` un objeto.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parámetros

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor gopher.

*pstrUserName*<br/>
Puntero a una cadena que contiene el nombre de usuario.

*pstrPassword*<br/>
Puntero a una cadena que contiene la contraseña de acceso.

*nPort*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) . Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

### <a name="remarks"></a>Comentarios

`GetGopherConnection`se conecta a un servidor gopher y crea y devuelve un puntero a un `CGopherConnection` objeto. No realiza ninguna operación específica en el servidor. Si piensa leer o escribir datos, por ejemplo, debe realizar dichas operaciones como pasos independientes. Vea las clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile (](../../mfc/reference/cgopherfile-class.md)y [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) para obtener información sobre cómo buscar archivos, abrir archivos y leer o escribir en archivos. Para obtener información sobre cómo examinar un sitio FTP, vea la función miembro [OpenURL](#openurl). Vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos para realizar tareas comunes de conexión de Gopher.

## <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection

Llame a esta función miembro para establecer una conexión http y obtener un puntero a `CHttpConnection` un objeto.

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>Parámetros

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor HTTP.

*nPort*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

*pstrUserName*<br/>
Puntero a una cadena que contiene el nombre de usuario.

*pstrPassword*<br/>
Puntero a una cadena que contiene la contraseña de acceso.

*dwflags*<br/>
Cualquier combinación de las `INTERNET_FLAG_*` marcas. Vea la tabla en la sección **comentarios** de [CHttpConnection (:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) para obtener una descripción de los valores *dwFlags* .

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) . Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

### <a name="remarks"></a>Comentarios

`GetHttpConnection`se conecta a un servidor http y crea y devuelve un puntero a un `CHttpConnection` objeto. No realiza ninguna operación específica en el servidor. Si piensa consultar un encabezado HTTP, por ejemplo, debe realizar esta operación como un paso independiente. Vea las clases [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) y [CHttpFile](../../mfc/reference/chttpfile-class.md) para obtener información acerca de las operaciones que puede realizar mediante una conexión a un servidor http. Para obtener información sobre cómo examinar un sitio HTTP, vea la función miembro [OpenURL](#openurl). Vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos para realizar tareas comunes de conexión http.

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

El marco de trabajo llama a esta función miembro para actualizar el estado cuando está habilitada la devolución de llamada de estado y hay una operación pendiente.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parámetros

*dwContext*<br/>
Valor de contexto proporcionado por la aplicación.

*dwInternetStatus*<br/>
Un código de estado que indica por qué se realiza la devolución de llamada. Vea la **sección Comentarios** para obtener una tabla de valores posibles.

*lpvStatusInformation*<br/>
Un puntero a un búfer que contiene información pertinente a esta devolución de llamada.

*dwStatusInformationLength*<br/>
Tamaño de *lpvStatusInformation*.

### <a name="remarks"></a>Comentarios

Primero debe llamar a [EnableStatusCallback](#enablestatuscallback) para aprovechar las ventajas de la devolución de llamada de estado.

El parámetro *dwInternetStatus* indica la operación que se está llevando a cabo y determina cuál será el contenido de *lpvStatusInformation* . *dwStatusInformationLength* indica la longitud de los datos incluidos en *lpvStatusInformation*. Los siguientes valores de estado para *dwInternetStatus* se definen de la siguiente manera:

|Valor|Significado|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Buscar la dirección IP del nombre incluido en *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Se encontró correctamente la dirección IP del nombre contenido en *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Conexión a la dirección de socket ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) a la que apunta *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Se conectó correctamente a la dirección de socket (SOCKADDR) a la que apunta *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Enviar la solicitud de información al servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_ REQUEST_SENT|La solicitud de información se envió correctamente al servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Esperando a que el servidor responda a una solicitud. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Se recibió correctamente una respuesta del servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Cerrando la conexión con el servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|La conexión se cerró correctamente en el servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Lo utiliza la función [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) de la API de Win32 para indicar que ha creado el nuevo identificador. Esto permite que la aplicación llame a la función [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) de Win32 desde otro subproceso si la conexión está tardando demasiado. Vea el SDKfor de Windows para obtener más información acerca de estas funciones.|
|INTERNET_STATUS_HANDLE_CLOSING|Se terminó correctamente este valor de identificador.|

Invalide esta función miembro para requerir alguna acción antes de que se realice una rutina de devolución de llamada de estado.

> [!NOTE]
> Las devoluciones de llamada de estado necesitan protección de estado de subprocesos. Si está utilizando MFC en una biblioteca compartida, agregue la siguiente línea al principio de la invalidación:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Para obtener más información acerca de las operaciones asincrónicas, [vea el artículo pasos de Internet First: WinInet](../../mfc/wininet-basics.md).

## <a name="openurl"></a>  CInternetSession::OpenURL

Llame a esta función miembro para enviar la solicitud especificada al servidor HTTP y permitir que el cliente especifique los encabezados RFC822, MIME o HTTP adicionales que se van a enviar junto con la solicitud.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Parámetros

*pstrURL*<br/>
Puntero al nombre de la dirección URL que se va a empezar a leer. Solo se admiten las direcciones URL que comienzan por File:, FTP:, Gopher: o http:. Valida si *pstrURL* es NULL.

*dwContext*<br/>
Un valor definido por la aplicación que se pasa con el identificador devuelto en la devolución de llamada.

*dwFlags*<br/>
Marcas que describen cómo controlar esta conexión. Vea la **sección Comentarios** para obtener más información sobre las marcas válidas. Las marcas válidas son:

- INTERNET_FLAG_TRANSFER_ASCII el valor predeterminado. Transfiera el archivo como texto ASCII.

- INTERNET_FLAG_TRANSFER_BINARY transfiera el archivo como un archivo binario.

- INTERNET_FLAG_RELOAD obtiene los datos de la conexión incluso si se almacenan en caché localmente.

- INTERNET_FLAG_DONT_CACHE no almacenan en caché los datos, ya sea de forma local o en cualquier puerta de enlace.

- INTERNET_FLAG_SECURE esta marca solo es aplicable a las solicitudes HTTP. Solicita transacciones seguras en la conexión con Capa de sockets seguros o PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT si es posible, reutilice las conexiones existentes al servidor para las nuevas solicitudes `OpenUrl` generadas por en lugar de crear una nueva sesión para cada solicitud de conexión.

- INTERNET_FLAG_PASSIVE usado para un sitio FTP. Usa semántica de FTP pasivo. Se usa con [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) de `OpenURL`.

*pstrHeaders*<br/>
Puntero a una cadena que contiene los encabezados que se van a enviar al servidor HTTP.

*dwHeadersLength*<br/>
La longitud, en caracteres, de los encabezados adicionales. Si este es-1L y *pstrHeaders* no es null, se supone que el valor de *pstrHeaders* es cero y se calcula la longitud.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo para los servicios de Internet FTP, GOPHER, HTTP y tipo de archivo únicamente. Devuelve NULL si el análisis no se ha realizado correctamente.

El puntero que `OpenURL` devuelve depende del tipo de servicio de *pstrURL*. En la tabla siguiente se muestran los posibles punteros `OpenURL` que pueden devolver.

|Tipo de dirección URL|Devuelve|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>Comentarios

El parámetro *dwFlags* debe incluir INTERNET_FLAG_TRANSFER_ASCII o INTERNET_FLAG_TRANSFER_BINARY, pero no ambos. Las marcas restantes se pueden combinar con **el operador OR** bit a **&#124;** bit ().

`OpenURL`, que ajusta la función `InternetOpenURL`de Win32, solo permite descargar, recuperar y leer los datos de un servidor de Internet. `OpenURL`no permite la manipulación de archivos en una ubicación remota, por lo que no requiere ningún objeto [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) .

Para usar funciones específicas de la conexión (es decir, específicas del Protocolo), como escribir en un archivo, debe abrir una sesión, abrir un determinado tipo de conexión y, a continuación, usar esa conexión para abrir un archivo en el modo deseado. Vea `CInternetConnection` para obtener más información sobre las funciones específicas de la conexión.

## <a name="operator_hinternet"></a>CInternetSession:: Operator HINTERNET

Utilice este operador para obtener el identificador de Windows para la sesión de Internet actual.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

Establece una cookie para la dirección URL especificada.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Un puntero a una cadena terminada en null que especifica la dirección URL para la que se debe establecer la cookie.

*pstrCookieName*<br/>
Puntero a una cadena que contiene el nombre de la cookie.

*pstrCookieData*<br/>
Puntero a una cadena que contiene los datos de cadena reales que se van a asociar a la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, o FALSE en caso contrario. Para obtener el código de error específico, llame a.`GetLastError.`

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), tal y como se describe en el Windows SDK.

## <a name="setoption"></a>  CInternetSession::SetOption

Llame a esta función miembro para establecer las opciones de la sesión de Internet.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*dwOption*<br/>
Opción de Internet que se va a establecer. Vea [marcas de opciones](/windows/win32/WinInet/option-flags) en la SDKfor de Windows lista de las posibles opciones.

*lpBuffer*<br/>
Búfer que contiene el valor de la opción.

*dwBufferLength*<br/>
La longitud de *lpBuffer* o el tamaño de *dwValue*.

*dwValue*<br/>
DWORD que contiene el valor de la opción.

*dwFlags*<br/>
Indica varias opciones de almacenamiento en caché. El valor predeterminado se establece en 0. Los valores posibles son:

- INTERNET_FLAG_DONT_CACHE no almacenan en caché los datos, ya sea de forma local o en cualquier servidor de puerta de enlace.

- Las operaciones de descarga de INTERNET_FLAG_OFFLINE solo se satisfacen a través de la caché persistente. Si el elemento no existe en la memoria caché, se devuelve un código de error adecuado. Esta marca se puede combinar con el operador bit a **&#124;** bit or ().

### <a name="return-value"></a>Valor devuelto

Si la operación se realizó correctamente, se devuelve el valor TRUE. Si se produce un error, se devuelve el valor FALSE. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection (clase)](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
