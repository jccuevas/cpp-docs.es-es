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
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372383"
---
# <a name="cinternetsession-class"></a>CInternetSession (clase)

Crea e inicializa una o varias sesiones de Internet simultáneas y, si es necesario, describe la conexión a un servidor proxy.

## <a name="syntax"></a>Sintaxis

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Construye un objeto `CInternetSession`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetSession::Cerrar](#close)|Cierra la conexión a Internet cuando finaliza la sesión de Internet.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Establece una rutina de devolución de llamada de estado.|
|[CInternetSession::GetContext](#getcontext)|Cierra la conexión a Internet cuando finaliza la sesión de Internet.|
|[CInternetSession::GetCookie](#getcookie)|Devuelve cookies para la URL especificada y todas sus URL principales.|
|[CInternetSession::GetCookieLength](#getcookielength)|Recupera la variable que especifica la longitud de la cookie almacenada en el búfer.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Abre una sesión FTP con un servidor. Inicia sesión en el usuario.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Abre un servidor gopher para una aplicación que está intentando abrir una conexión.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Abre un servidor HTTP para una aplicación que intenta abrir una conexión.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Actualiza el estado de una operación cuando la devolución de llamada de estado está habilitada.|
|[CInternetSession::OpenURL](#openurl)|Analiza y abre una dirección URL.|
|[CInternetSession::SetCookie](#setcookie)|Establece una cookie para la dirección URL especificada.|
|[CInternetSession::SetOption](#setoption)|Establece las opciones para la sesión de Internet.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetSession::operador HINTERNET](#operator_hinternet)|Un identificador de la sesión de Internet actual.|

## <a name="remarks"></a>Observaciones

Si la conexión a Internet debe mantenerse durante la `CInternetSession` duración de una aplicación, puede crear un miembro de la clase [CWinApp](../../mfc/reference/cwinapp-class.md).

Una vez que haya establecido una sesión de Internet, puede llamar a [OpenURL](#openurl). `CInternetSession`A continuación, analiza la dirección URL mediante una llamada a la función global [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Independientemente de su `CInternetSession` tipo de protocolo, interpreta la dirección URL y la administra por usted. Puede gestionar las solicitudes de archivos locales identificados con el recurso de dirección URL "file://". `OpenURL`devolverá un puntero a un [CStdioFile](../../mfc/reference/cstdiofile-class.md) objeto si el nombre que se pasa es un archivo local.

Si abre una dirección URL `OpenURL`en un servidor de Internet mediante , puede leer la información del sitio. Si desea realizar acciones específicas del servicio (por ejemplo, HTTP, FTP o gopher) en archivos ubicados en un servidor, debe establecer la conexión adecuada con ese servidor. Para abrir un tipo determinado de conexión directamente a un servicio determinado, utilice una de las siguientes funciones miembro:

- [GetGopherConnection](#getgopherconnection) para abrir una conexión a un servicio gopher.

- [GetHttpConnection](#gethttpconnection) para abrir una conexión a un servicio HTTP.

- [GetFtpConnection](#getftpconnection) para abrir una conexión a un servicio FTP.

[SetOption](#setoption) le permite establecer las opciones de consulta de la sesión, como los valores de tiempo de espera, el número de reintentos, etc.

`CInternetSession`Las funciones miembro [SetCookie](#setcookie), [GetCookie](#getcookie)y [GetCookieLength](#getcookielength) proporcionan los medios para administrar una base de datos de cookies Win32, a través de la cual los servidores y scripts mantienen información de estado sobre la estación de trabajo cliente.

Para obtener más información acerca de las tareas básicas de programación de Internet, consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md). Para obtener información general sobre el uso de las clases WinInet de MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`producirá una [excepción AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) para los tipos de servicio no admitidos. Actualmente solo se admiten los siguientes tipos de servicio: FTP, HTTP, gopher y file.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>CInternetSession::CInternetSession

Se llama a esta `CInternetSession` función miembro cuando se crea un objeto.

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
Puntero a una cadena que identifica el nombre de la aplicación o entidad que llama a las funciones de Internet (por ejemplo, "Microsoft Internet Browser"). Si *pstrAgent* es NULL (valor predeterminado), el marco de trabajo llama a la función global [AfxGetAppName](application-information-and-management.md#afxgetappname), que devuelve una cadena terminada en null que contiene el nombre de una aplicación. Algunos protocolos usan esta cadena para identificar la aplicación en el servidor.

*dwContext*<br/>
Identificador de contexto para la operación. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession::OnStatusCallback](#onstatuscallback). El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que realice se asociarán con ese identificador de contexto.

*dwAccessType*<br/>
El tipo de acceso requerido. Los siguientes son valores válidos, exactamente uno de los cuales se puede suministrar:

- INTERNET_OPEN_TYPE_PRECONFIG Conectar mediante la configuración preconfigurada en el registro. Este tipo de acceso se establece como predeterminado. Para conectarse a través de un proxy TIS, establezca *dwAccessType* en este valor; a continuación, establezca el registro de forma adecuada.

- INTERNET_OPEN_TYPE_DIRECT Conéctese directamente a Internet.

- INTERNET_OPEN_TYPE_PROXY Conectar a través de un proxy CERN.

Para obtener información sobre cómo conectarse con diferentes tipos de servidores proxy, consulte [Pasos en una aplicación cliente FTP típica.](../../mfc/steps-in-a-typical-ftp-client-application.md)

*pstrProxyName*<br/>
El nombre del proxy CERN preferido si *dwAccessType* se establece como INTERNET_OPEN_TYPE_PROXY. El valor predeterminado es NULL.

*pstrProxyBypass*<br/>
Puntero a una cadena que contiene una lista opcional de direcciones de servidor. Estas direcciones se pueden omitir cuando se utiliza el acceso de proxy. Si se proporciona un valor NULL, la lista de omisión se leerá del registro. Este parámetro solo es significativo si *dwAccessType* se establece en INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Indica varias opciones de almacenamiento en caché. El valor predeterminado se establece en 0. Los valores posibles incluyen:

- INTERNET_FLAG_DONT_CACHE No almacene en caché los datos, ya sea localmente o en ningún servidor de puerta de enlace.

- INTERNET_FLAG_OFFLINE las operaciones de descarga solo se satisfacen a través de la memoria caché persistente. Si el elemento no existe en la memoria caché, se devuelve un código de error adecuado. Este indicador se puede combinar con el operador **OR** ( **&#124;**) bit a bit.

### <a name="remarks"></a>Observaciones

`CInternetSession`es la primera función de Internet llamada por una aplicación. Inicializa las estructuras de datos internas y se prepara para futuras llamadas desde la aplicación.

Si no se puede `CInternetSession` abrir ninguna conexión a Internet, inicia una [excepción AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionclose"></a><a name="close"></a>CInternetSession::Cerrar

Llame a esta función miembro `CInternetSession` cuando la aplicación haya terminado de usar el objeto.

```cpp
virtual void Close();
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Llame a esta función miembro para habilitar la devolución de llamada de estado.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Especifica si la devolución de llamada está habilitada o deshabilitada. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

### <a name="remarks"></a>Observaciones

Al controlar la devolución de llamada de estado, puede proporcionar el estado sobre el progreso de la operación (como resolver el nombre, conectarse al servidor, etc.) en la barra de estado de la aplicación. La visualización del estado de la operación es especialmente deseable durante una operación a largo plazo.

Dado que las devoluciones de llamada se producen durante el procesamiento de la solicitud, la aplicación debe pasar el menor tiempo posible en la devolución de llamada para evitar la degradación del rendimiento de datos en la red. Por ejemplo, colocar un cuadro de diálogo en una devolución de llamada puede ser una operación tan larga que el servidor finaliza la solicitud.

La devolución de llamada de estado no se puede quitar siempre y cuando haya devoluciones de llamada pendientes.

Para controlar las operaciones de forma asincrónica, debe crear su propio subproceso o usar las funciones WinInet sin MFC.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>CInternetSession::GetContext

Llame a esta función miembro para obtener el valor de contexto para una sesión de aplicación determinada.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de contexto definido por la aplicación.

### <a name="remarks"></a>Observaciones

[OnStatusCallback](#onstatuscallback) utiliza el identificador `GetContext` de contexto devuelto por para informar del estado de una aplicación determinada. Por ejemplo, cuando un usuario activa una solicitud de Internet que implica devolver información de estado, la devolución de llamada de estado usa el identificador de contexto para notificar el estado de esa solicitud concreta. Si el usuario activa dos solicitudes de Internet independientes que implican la devolución de información de estado, `OnStatusCallback` utiliza los identificadores de contexto para devolver el estado sobre sus solicitudes correspondientes. Por lo tanto, el identificador de contexto se utiliza para todas las operaciones de devolución de llamada de estado y se asocia a la sesión hasta que finaliza la sesión.

Para obtener más información acerca de las operaciones asincrónicas, vea el artículo Pasos primero de [Internet: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>CInternetSession::GetCookie

Esta función miembro implementa el comportamiento de la función de Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), como se describe en el Windows SDK.

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
Puntero a una cadena que contiene el nombre de la cookie para obtener la dirección URL especificada.

*pstrCookieData*<br/>
En la primera sobrecarga, un puntero a una cadena que contiene la dirección del búfer que recibe los datos de cookie. Este valor puede ser NULL. En la segunda sobrecarga, una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para recibir los datos de cookie.

*dwBufLen*<br/>
Variable que especifica el tamaño del búfer *pstrCookieData.* Si la función se realiza correctamente, el búfer recibe la cantidad de datos copiados en el búfer *pstrCookieData.* Si *pstrCookieData* es NULL, este parámetro recibe un valor que especifica el tamaño del búfer necesario para copiar todos los datos de cookies.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente o FALSE en caso contrario. Si se produce un error en la llamada, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error. Se aplican los siguientes valores de error:

- ERROR_NO_MORE_ITEMS No hay ninguna cookie para la URL especificada y todos sus padres.

- ERROR_INSUFFICIENT_BUFFER El valor pasado en *dwBufLen* es insuficiente para copiar todos los datos de cookies. El valor devuelto en *dwBufLen* es el tamaño del búfer necesario para obtener todos los datos.

### <a name="remarks"></a>Observaciones

En la segunda sobrecarga, MFC recupera los `CString` datos de cookie en el objeto proporcionado.

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>CInternetSession::GetCookieLength

Llame a esta función miembro para obtener la longitud de la cookie almacenada en el búfer.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Un puntero a una cadena que contiene la dirección URL

*pstrCookieName*<br/>
Puntero a una cadena que contiene el nombre de la cookie.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que indica la longitud de la cookie, almacenada en el búfer. Cero si no existe ninguna cookie con el nombre indicado por *pstrCookieName.*

### <a name="remarks"></a>Observaciones

[GetCookie](#getcookie)utiliza este valor.

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>CInternetSession::GetFtpConnection

Llame a esta función miembro para establecer `CFtpConnection` una conexión FTP y obtener un puntero a un objeto.

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
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se usará para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL (o una cadena vacía) pero *pstrUserName* no es NULL, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword:*

| *pstrUserName*  | *pstrPassword*  | Nombre de usuario enviado al servidor FTP | Contraseña enviada al servidor FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL o " "   |   NULL o " "   |         "anónimo"         |      Nombre de correo electrónico del usuario      |
| Cadena no NULL |   NULL o " "   |       *pstrUserName*        |             " "             |
|      NULL       | Cadena no NULL |            ERROR            |            ERROR            |
| Cadena no NULL | Cadena no NULL |       *pstrUserName*        |       *pstrPassword*        |

*Nport*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

*bPasivo*<br/>
Especifica el modo pasivo o activo para esta sesión FTP. Si se establece en TRUE, establece `dwFlag` la API de Win32 en INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CFtpConnection](../../mfc/reference/cftpconnection-class.md) objeto. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

### <a name="remarks"></a>Observaciones

`GetFtpConnection`se conecta a un servidor FTP y `CFTPConnection` crea y devuelve un puntero a un objeto. No realiza ninguna operación específica en el servidor. Si tiene la intención de leer o escribir en archivos, por ejemplo, debe realizar esas operaciones como pasos independientes. Consulte las clases [CFtpConnection](../../mfc/reference/cftpconnection-class.md) y [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) para obtener información sobre la búsqueda de archivos, la apertura de archivos y la lectura o escritura en archivos. Consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos para realizar tareas comunes de conexión FTP.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Llame a esta función miembro para establecer una nueva `CGopherConnection` conexión gopher y obtener un puntero a un objeto.

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

*Nport*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

### <a name="remarks"></a>Observaciones

`GetGopherConnection`se conecta a un servidor gopher y `CGopherConnection` crea y devuelve un puntero a un objeto. No realiza ninguna operación específica en el servidor. Si tiene la intención de leer o escribir datos, por ejemplo, debe realizar esas operaciones como pasos independientes. Consulte las clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)y [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) para obtener información sobre la búsqueda de archivos, la apertura de archivos y la lectura o escritura en archivos. Para obtener información sobre cómo examinar un sitio FTP, consulte la función miembro [OpenURL](#openurl). Consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos para realizar tareas comunes de conexión de gopher.

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Llame a esta función miembro para establecer `CHttpConnection` una conexión HTTP y obtener un puntero a un objeto.

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

*Nport*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

*pstrUserName*<br/>
Puntero a una cadena que contiene el nombre de usuario.

*pstrPassword*<br/>
Puntero a una cadena que contiene la contraseña de acceso.

*Dwflags*<br/>
Cualquier combinación `INTERNET_FLAG_*` de las banderas. Consulte la tabla de la sección **Comentarios** de [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) para obtener una descripción de los valores *dwFlags.*

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objeto. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

### <a name="remarks"></a>Observaciones

`GetHttpConnection`se conecta a un servidor HTTP y `CHttpConnection` crea y devuelve un puntero a un objeto. No realiza ninguna operación específica en el servidor. Si tiene la intención de consultar un encabezado HTTP, por ejemplo, debe realizar esta operación como un paso independiente. Consulte las clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CHttpFile](../../mfc/reference/chttpfile-class.md) para obtener información sobre las operaciones que puede realizar mediante una conexión a un servidor HTTP. Para obtener información sobre cómo examinar un sitio HTTP, consulte la función miembro [OpenURL](#openurl). Consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos para realizar tareas de conexión HTTP comunes.

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

El marco de trabajo llama a esta función miembro para actualizar el estado cuando se habilita la devolución de llamada de estado y una operación está pendiente.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parámetros

*dwContext*<br/>
El valor de contexto proporcionado por la aplicación.

*dwInternetStatus*<br/>
Un código de estado que indica por qué se realiza la devolución de llamada. Consulte **Comentarios** para obtener una tabla de valores posibles.

*lpvStatusInformation*<br/>
Puntero a un búfer que contiene información pertinente a esta devolución de llamada.

*dwStatusInformationLength*<br/>
El tamaño de *lpvStatusInformation*.

### <a name="remarks"></a>Observaciones

Primero debe llamar a [EnableStatusCallback](#enablestatuscallback) para aprovechar la devolución de llamada de estado.

El parámetro *dwInternetStatus* indica la operación que se está realizando y determina cuál será el contenido de *lpvStatusInformation.* *dwStatusInformationLength* indica la longitud de los datos incluidos en *lpvStatusInformation*. Los siguientes valores de estado para *dwInternetStatus* se definen de la siguiente manera:

|Value|Significado|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Buscando la dirección IP del nombre contenido en *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Se ha encontrado correctamente la dirección IP del nombre contenido en *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Conexión a la dirección de socket ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) a la que apunta *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Conectado correctamente a la dirección de socket (SOCKADDR) a la que apunta *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Enviar la solicitud de información al servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Se ha enviado correctamente la solicitud de información al servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Esperando a que el servidor responda a una solicitud. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Recibió correctamente una respuesta del servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Cierre de la conexión al servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Se ha cerrado correctamente la conexión con el servidor. El parámetro *lpvStatusInformation* es NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Utilizado por la función de API de Win32 [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) para indicar que ha creado el nuevo identificador. Esto permite a la aplicación llamar a la función de Win32 [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) desde otro subproceso si la conexión está tardando demasiado. Consulte el SDK de Windows para obtener más información acerca de estas funciones.|
|INTERNET_STATUS_HANDLE_CLOSING|Se ha terminado correctamente este valor de identificador.|

Invalide esta función miembro para requerir alguna acción antes de que se realice una rutina de devolución de llamada de estado.

> [!NOTE]
> Las devoluciones de llamada de estado necesitan protección de estado de subproceso. Si utiliza MFC en una biblioteca compartida, agregue la siguiente línea al principio de la invalidación:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Para obtener más información acerca de las operaciones asincrónicas, vea el artículo Pasos primero de [Internet: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>CInternetSession::OpenURL

Llame a esta función miembro para enviar la solicitud especificada al servidor HTTP y permitir que el cliente especifique encabezados RFC822, MIME o HTTP adicionales para enviar junto con la solicitud.

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
Un puntero al nombre de la dirección URL para comenzar a leer. Solo se admiten las direcciones URL que comienzan con file:, ftp:, gopher: o http:. Afirma si *pstrURL* es NULL.

*dwContext*<br/>
Un valor definido por la aplicación pasado con el identificador devuelto en la devolución de llamada.

*dwFlags*<br/>
Los indicadores que describen cómo controlar esta conexión. Consulte **Comentarios** para obtener más información sobre las marcas válidas. Los indicadores válidos son:

- INTERNET_FLAG_TRANSFER_ASCII El valor predeterminado. Transfiera el archivo como texto ASCII.

- INTERNET_FLAG_TRANSFER_BINARY Transferir el archivo como un archivo binario.

- INTERNET_FLAG_RELOAD Obtener los datos de la conexión incluso si se almacena localmente en caché.

- INTERNET_FLAG_DONT_CACHE No almacene en caché los datos, ya sea localmente o en ninguna puerta de enlace.

- INTERNET_FLAG_SECURE Esta marca solo es aplicable a las solicitudes HTTP. Solicita transacciones seguras en el cable con Secure Sockets Layer o PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Si es posible, reutilice las conexiones existentes `OpenUrl` al servidor para las nuevas solicitudes generadas por en lugar de crear una nueva sesión para cada solicitud de conexión.

- INTERNET_FLAG_PASSIVE Se utiliza para un sitio FTP. Utiliza la semántica FTP pasiva. Se utiliza con `OpenURL` [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) de .

*pstrHeaders*<br/>
Puntero a una cadena que contiene los encabezados que se enviarán al servidor HTTP.

*dwHeadersLength*<br/>
La longitud, en caracteres, de los encabezados adicionales. Si se trata de -1L y *pstrHeaders* no ES NULL, se supone que *pstrHeaders* está terminado en cero y se calcula la longitud.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo solo para servicios de Internet de tipo FTP, GOPHER, HTTP y FILE. Devuelve NULL si el análisis no se realizó correctamente.

El puntero `OpenURL` que devuelve depende del tipo de servicio *pstrURL*. La tabla siguiente ilustra los `OpenURL` posibles punteros que pueden devolver.

|Tipo de URL|Devuelve|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>Observaciones

El parámetro *dwFlags* debe incluir INTERNET_FLAG_TRANSFER_ASCII o INTERNET_FLAG_TRANSFER_BINARY, pero no ambos. Los indicadores restantes se pueden combinar con el operador **OR** bit a bit ( **&#124;**).

`OpenURL`, que envuelve la `InternetOpenURL`función Win32, solo permite descargar, recuperar y leer los datos de un servidor de Internet. `OpenURL`no permite ninguna manipulación de archivos en una ubicación remota, por lo que no requiere ningún objeto [CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

Para utilizar funciones específicas de la conexión (es decir, específicas del protocolo), como escribir en un archivo, debe abrir una sesión,, a continuación, abrir un tipo determinado de conexión y, a continuación, utilizar esa conexión para abrir un archivo en el modo deseado. Consulte `CInternetConnection` para obtener más información acerca de las funciones específicas de la conexión.

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetSession::operador HINTERNET

Utilice este operador para obtener el identificador de Windows para la sesión de Internet actual.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>CInternetSession::SetCookie

Establece una cookie para la dirección URL especificada.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Puntero a una cadena terminada en null que especifica la dirección URL para la que se debe establecer la cookie.

*pstrCookieName*<br/>
Puntero a una cadena que contiene el nombre de la cookie.

*pstrCookieData*<br/>
Puntero a una cadena que contiene los datos de cadena reales que se van a asociar a la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente o FALSE en caso contrario. Para obtener el código de error específico, llame`GetLastError.`

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), como se describe en el Windows SDK.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>CInternetSession::SetOption

Llame a esta función miembro para establecer opciones para la sesión de Internet.

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
La opción de Internet para establecer. Consulte Marcas de [opciones](/windows/win32/WinInet/option-flags) en el SDK de Windows para obtener una lista de las opciones posibles.

*lpBuffer*<br/>
Un búfer que contiene la configuración de la opción.

*dwBufferLength*<br/>
La longitud de *lpBuffer* o el tamaño de *dwValue*.

*dwValue*<br/>
Un DWORD que contiene la configuración de la opción.

*dwFlags*<br/>
Indica varias opciones de almacenamiento en caché. El valor predeterminado se establece en 0. Los valores posibles incluyen:

- INTERNET_FLAG_DONT_CACHE No almacene en caché los datos, ya sea localmente o en ningún servidor de puerta de enlace.

- INTERNET_FLAG_OFFLINE las operaciones de descarga solo se satisfacen a través de la memoria caché persistente. Si el elemento no existe en la memoria caché, se devuelve un código de error adecuado. Este indicador se puede combinar con el operador **OR** ( **&#124;**) bit a bit.

### <a name="return-value"></a>Valor devuelto

Si la operación se realizó correctamente, se devuelve un valor de TRUE. Si se ha producido un error, se devuelve un valor de FALSE. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)<br/>
[Clase CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
