---
title: CGopherConnection (clase)
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
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373711"
---
# <a name="cgopherconnection-class"></a>CGopherConnection (clase)

Administra la conexión a un servidor de Internet de gopher.

> [!NOTE]
> Las `CGopherConnection`clases `CGopherFileFind` `CGopherLocator` , `CGopherFile`, , y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Construye un objeto `CGopherConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Crea un [cGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto para buscar archivos en un servidor gopher.|
|[CGopherConnection::GetAttribute](#getattribute)|Recupera información de atributos sobre el objeto gopher.|
|[CGopherConnection::OpenFile](#openfile)|Abre un archivo gopher.|

## <a name="remarks"></a>Observaciones

El servicio gopher es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.

La `CGopherConnection` clase contiene un constructor y tres funciones miembro adicionales que administran el servicio gopher: [OpenFile](#openfile), [CreateLocator](#createlocator)y [GetAttribute](#getattribute).

Para comunicarse con un servidor de Internet gopher, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, `CGopherConnection` a continuación, llamar a [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea el objeto y devuelve un puntero a él. Nunca se `CGopherConnection` crea un objeto directamente.

Para obtener más `CGopherConnection` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre el uso de los otros dos servicios de Internet compatibles, FTP y HTTP, consulte las clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Esta función miembro se `CGopherConnection` llama para construir un objeto.

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
Un puntero al objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) relacionado.

*hConectado*<br/>
El identificador de Windows de la sesión de Internet actual.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor FTP.

*dwContext*<br/>
Identificador de contexto para la operación. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que realice se asociarán con ese identificador de contexto.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se usará para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL (o una cadena vacía) pero *pstrUserName* no es NULL, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword:*

|*pstrUserName*|*pstrPassword*|Nombre de usuario enviado al servidor FTP|Contraseña enviada al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o " "|NULL o " "|"anónimo"|Nombre de correo electrónico del usuario|
|Cadena no NUNULL|NULL o " "|*pstrUserName*|" "|
|NULL Non- NULL String|ERROR|ERROR||
|Cadena no NUNULL|Cadena no NUNULL|*pstrUserName*|*pstrPassword*|

*Nport*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

### <a name="remarks"></a>Observaciones

Nunca se `CGopherConnection` crea un directamente. En su lugar, llame a [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea un `CGopherConnection` objeto y devuelve un puntero a él.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>CGopherConnection::CreateLocator

Llame a esta función miembro para crear un localizador gopher para buscar o identificar un archivo en un servidor gopher.

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
Puntero a una cadena que contiene el nombre del documento o directorio gopher que se va a recuperar. Si el *pstrDisplayString* parámetro es NULL, se devuelve el directorio predeterminado para el servidor gopher.

*pstrSelectorString*<br/>
Un puntero a la cadena del selector que se enviará al servidor gopher para recuperar un elemento. *pstrSelectorString* puede ser NULL.

*dwGopherType*<br/>
Esto especifica si *pstrSelectorString* hace referencia a un directorio o documento y si la solicitud es gopher o gopher+. Consulte los atributos de la [estructura GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) en el Windows SDK.

*pstrLocator*<br/>
Puntero a una cadena que identifica el archivo que se va a abrir. Por lo general, esta cadena se devuelve de una llamada a [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Puntero a una cadena que contiene el nombre del servidor gopher.

*Nport*<br/>
El número que identifica el puerto de Internet para esta conexión.

### <a name="return-value"></a>Valor devuelto

Un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

### <a name="remarks"></a>Observaciones

La versión estática de la función miembro requiere que especifique un servidor, mientras que la versión no estática utiliza el nombre de servidor del objeto de conexión.

Para recuperar información de un servidor gopher, una aplicación primero debe obtener un localizador gopher. A continuación, la aplicación debe tratar el localizador como un token opaco (es decir, la aplicación puede usar el localizador, pero no manipularlo ni compararlo directamente). Normalmente, la aplicación utiliza el localizador para las llamadas a la [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) función miembro para recuperar un elemento específico de información.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>CGopherConnection::GetAttribute

Llame a esta función miembro para recuperar información de atributo específica sobre un elemento del servidor gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parámetros

*refLocator*<br/>
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*strRequestedAttributes*<br/>
Cadena delimitada por espacios que especifica los nombres de los atributos solicitados.

*strResult*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que recibe el tipo de localizador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>CGopherConnection::OpenFile

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
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*dwFlags*<br/>
Cualquier combinación de indicadores INTERNET_FLAG_*. Consulte [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) para obtener\* más información sobre INTERNET_FLAG_ marcas.

*pstrView*<br/>
Puntero a una cadena de vista de archivo. Si existen varias vistas del archivo en el servidor, este parámetro especifica qué vista de archivo se va a abrir. Si *pstrView* es NULL, se utiliza la vista de archivo predeterminada.

*dwContext*<br/>
El identificador de contexto del archivo que se está abrendo. Consulte **Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CGopherFile](../../mfc/reference/cgopherfile-class.md) objeto que se va a abrir.

### <a name="remarks"></a>Observaciones

Invalide el valor predeterminado *dwContext* para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado `CGopherConnection` a esta operación específica del objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="see-also"></a>Consulte también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Clase CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Clase CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
