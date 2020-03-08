---
title: Clase CGopherConnection
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883907"
---
# <a name="cgopherconnection-class"></a>Clase CGopherConnection

Administra la conexión a un servidor de Internet de gopher.

> [!NOTE]
>  Las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros están desusadas porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Construye un objeto `CGopherConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherConnection:: CreateLocator](#createlocator)|Crea un objeto [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) para buscar archivos en un servidor gopher.|
|[CGopherConnection:: GetAttribute](#getattribute)|Recupera información de atributos sobre el objeto Gopher.|
|[CGopherConnection:: OpenFile](#openfile)|Abre un archivo Gopher.|

## <a name="remarks"></a>Observaciones

El servicio Gopher es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.

La clase `CGopherConnection` contiene un constructor y tres funciones miembro adicionales que administran el servicio Gopher: [OpenFile](#openfile), [CreateLocator](#createlocator)y [getAttribute](#getattribute).

Para comunicarse con un servidor de Internet Gopher, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, llamar a [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea el objeto `CGopherConnection` y devuelve un puntero a él. Nunca se crea un objeto `CGopherConnection` directamente.

Para obtener más información sobre cómo funciona `CGopherConnection` con las otras clases de Internet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre el uso de los otros dos servicios de Internet compatibles, FTP y HTTP, vea las clases [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Se llama a esta función miembro para construir un objeto `CGopherConnection`.

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parámetros

*pSession*<br/>
Puntero al objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) relacionado.

*hConnected*<br/>
Identificador de Windows de la sesión de Internet actual.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor FTP.

*dwContext*<br/>
Identificador de contexto para la operación. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que tenga se asociarán a ese identificador de contexto.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario en el que se va a iniciar sesión. Si es NULL, el valor predeterminado es Anonymous.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se va a usar para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es null (o una cadena vacía), pero *PSTRUSERNAME* no es null, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de los cuatro valores posibles de *pstrUserName* y *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nombre de usuario enviado al servidor FTP|Contraseña enviada al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o ""|NULL o ""|Anonymous|Nombre de correo electrónico del usuario|
|Cadena que no es NULL|NULL o ""|*pstrUserName*|" "|
|Cadena nula que no es NULL|ERROR|ERROR||
|Cadena que no es NULL|Cadena que no es NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

### <a name="remarks"></a>Observaciones

Nunca se crea un `CGopherConnection` directamente. En su lugar, llame a [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea un objeto `CGopherConnection` y devuelve un puntero a él.

##  <a name="createlocator"></a>CGopherConnection:: CreateLocator

Llame a esta función miembro para crear un localizador de Gopher para buscar o identificar un archivo en un servidor gopher.

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parámetros

*pstrDisplayString*<br/>
Un puntero a una cadena que contiene el nombre del documento o directorio Gopher que se va a recuperar. Si el parámetro *pstrDisplayString* es null, se devuelve el directorio predeterminado para el servidor gopher.

*pstrSelectorString*<br/>
Puntero a la cadena de selector que se va a enviar al servidor gopher para recuperar un elemento. *pstrSelectorString* puede ser null.

*dwGopherType*<br/>
Especifica si *pstrSelectorString* hace referencia a un directorio o un documento, y si la solicitud es Gopher o Gopher +. Vea los atributos de la estructura [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) en el Windows SDK.

*pstrLocator*<br/>
Puntero a una cadena que identifica el archivo que se va a abrir. Normalmente, esta cadena se devuelve de una llamada a [CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Puntero a una cadena que contiene el nombre del servidor gopher.

*nPort*<br/>
Número que identifica el puerto de Internet para esta conexión.

### <a name="return-value"></a>Valor devuelto

Objeto [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

### <a name="remarks"></a>Observaciones

La versión estática de la función miembro requiere que se especifique un servidor, mientras que la versión no estática utiliza el nombre del servidor del objeto de conexión.

Para recuperar información de un servidor gopher, una aplicación debe obtener primero un localizador de Gopher. A continuación, la aplicación debe tratar el localizador como un token opaco (es decir, la aplicación puede usar el localizador, pero no manipularlo ni compararlo directamente). Normalmente, la aplicación usa el localizador para las llamadas a la función miembro [CGopherFileFind:: findfile](../../mfc/reference/cgopherfilefind-class.md#findfile) para recuperar una parte específica de la información.

##  <a name="getattribute"></a>CGopherConnection:: GetAttribute

Llame a esta función miembro para recuperar información de atributos específica sobre un elemento del servidor gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parámetros

*refLocator*<br/>
Referencia a un objeto [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*strRequestedAttributes*<br/>
Cadena delimitada por espacios que especifica los nombres de los atributos solicitados.

*strResult*<br/>
Referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que recibe el tipo de localizador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

##  <a name="openfile"></a>CGopherConnection:: OpenFile

Llame a esta función miembro para abrir un archivo en un servidor gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*refLocator*<br/>
Referencia a un objeto [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*dwFlags*<br/>
Cualquier combinación de marcas de INTERNET_FLAG_* . Vea [CInternetSession:: OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) para obtener más información sobre las marcas de\* de INTERNET_FLAG_.

*pstrView*<br/>
Puntero a una cadena de vista de archivo. Si existen varias vistas del archivo en el servidor, este parámetro especifica la vista de archivo que se va a abrir. Si *pstrView* es null, se utiliza la vista de archivo predeterminada.

*dwContext*<br/>
IDENTIFICADOR de contexto para el archivo que se va a abrir. Vea la **sección Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto [CGopherFile (](../../mfc/reference/cgopherfile-class.md) que se va a abrir.

### <a name="remarks"></a>Observaciones

Invalide el valor predeterminado de *dwContext* para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado a esta operación específica del objeto `CGopherConnection` creado por su objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) . El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Vea el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="see-also"></a>Consulte también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection (clase)](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator (clase)](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
