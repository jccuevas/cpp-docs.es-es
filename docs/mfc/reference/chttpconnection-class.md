---
title: Clase CHttpConnection (
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 1941af1e16a897235dd90db509d6ed29c2d9a875
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425896"
---
# <a name="chttpconnection-class"></a>Clase CHttpConnection (

Administra la conexión a un servidor HTTP.

## <a name="syntax"></a>Sintaxis

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHttpConnection (:: CHttpConnection (](#chttpconnection)|Crea un objeto `CHttpConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHttpConnection (:: OpenRequest](#openrequest)|Abre una solicitud HTTP.|

## <a name="remarks"></a>Observaciones

HTTP es uno de los tres protocolos de servidor de Internet implementados por las clases WinInet de MFC.

La clase `CHttpConnection` contiene un constructor y una función miembro, [OpenRequest](#openrequest), que administra las conexiones a un servidor con un protocolo http.

Para comunicarse con un servidor HTTP, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, crear un objeto [CHttpConnection (](#chttpconnection) . Nunca se crea un objeto `CHttpConnection` directamente. en su lugar, llame a [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), que crea el objeto `CHttpConnection` y devuelve un puntero a él.

Para obtener más información sobre cómo funciona `CHttpConnection` con las otras clases de Internet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre cómo conectarse a los servidores mediante los otros dos protocolos de Internet compatibles, gopher y FTP, vea las clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="chttpconnection"></a>CHttpConnection (:: CHttpConnection (

Se llama a esta función miembro para construir un objeto `CHttpConnection`.

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pSession*<br/>
Un puntero a un objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Identificador de una conexión a Internet.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor.

*dwContext*<br/>
Identificador de contexto para el objeto de `CInternetConnection`. Para obtener más información sobre *dwContext*, consulte la sección **comentarios** .

*nPort*<br/>
Número que identifica el puerto de Internet para esta conexión.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario en el que se va a iniciar sesión. Si es NULL, el valor predeterminado es Anonymous.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se va a usar para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es null o una cadena vacía, pero *PSTRUSERNAME* no es null, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de los cuatro valores posibles de *pstrUserName* y *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nombre de usuario enviado al servidor FTP|Contraseña enviada al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o ""|NULL o ""|Anonymous|Nombre de correo electrónico del usuario|
|Cadena que no es NULL|NULL o ""|*pstrUserName*|" "|
|NULL |Cadena que no es NULL|ERROR|ERROR|
|Cadena que no es NULL|Cadena que no es NULL|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Cualquier combinación de las marcas de `INTERNET_FLAG_*`. Vea la tabla en la sección **comentarios** de [CHttpConnection (:: OpenRequest](#openrequest) para obtener una descripción de los valores *dwFlags* .

### <a name="remarks"></a>Observaciones

Nunca se crea un `CHttpConnection` directamente. En su lugar, cree un objeto llamando a [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

##  <a name="openrequest"></a>CHttpConnection (:: OpenRequest

Llame a esta función miembro para abrir una conexión HTTP.

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>Parámetros

*pstrVerb*<br/>
Puntero a una cadena que contiene el verbo que se va a utilizar en la solicitud. Si es NULL, se usa "GET".

*pstrObjectName*<br/>
Puntero a una cadena que contiene el objeto de destino del verbo especificado. Normalmente, esta cadena es un nombre de archivo, un módulo ejecutable o un especificador de búsqueda.

*pstrReferer*<br/>
Un puntero a una cadena que especifica la dirección (URL) del documento a partir del cual se obtuvo la dirección URL de la solicitud (*pstrObjectName*). Si es NULL, no se especifica ningún encabezado HTTP.

*dwContext*<br/>
Identificador de contexto para la operación `OpenRequest`. Para obtener más información sobre *dwContext*, consulte la sección Comentarios.

*ppstrAcceptTypes*<br/>
Puntero a una matriz terminada en NULL de punteros LPCTSTR a cadenas que indican los tipos de contenido aceptados por el cliente. Si *ppstrAcceptTypes* es null, los servidores interpretan que el cliente solo acepta documentos de tipo "Text/*" (es decir, solo documentos de texto, no imágenes u otros archivos binarios). El tipo de contenido es equivalente a la variable CONTENT_TYPE de CGI, que identifica el tipo de datos para las consultas que tienen información adjunta, como HTTP POST y PUT.

*pstrVersion*<br/>
Puntero a una cadena que define la versión de HTTP. Si es NULL, se utiliza "HTTP/1.0".

*dwFlags*<br/>
Cualquier combinación de las marcas INTERNET_ FLAG_*. Vea la sección Comentarios para obtener una descripción de los posibles valores de *dwFlags* .

*nVerb*<br/>
Número asociado al tipo de solicitud HTTP. Puede ser uno de los siguientes:

|Tipo de solicitud HTTP|valor *nVerb*|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Valor devuelto

Puntero al objeto [CHttpFile](../../mfc/reference/chttpfile-class.md) solicitado.

### <a name="remarks"></a>Observaciones

*dwFlags* puede ser uno de los siguientes:

|Marca de Internet|Descripción|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Fuerza una descarga del archivo, el objeto o el listado de directorio solicitado del servidor de origen, no de la memoria caché.|
|INTERNET_FLAG_DONT_CACHE|No agrega la entidad devuelta a la memoria caché.|
|INTERNET_FLAG_MAKE_PERSISTENT|Agrega la entidad devuelta a la memoria caché como una entidad persistente. Significa que la limpieza de caché estándar, la comprobación de coherencia o la recolección de elementos no utilizados no pueden quitar este elemento de la memoria caché.|
|INTERNET_FLAG_SECURE|Usa semántica de transacción segura. Se traduce en el uso de SSL/PCT y solo es significativo en las solicitudes HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Solo se usa con HTTP, especifica que las redirecciones no deben controlarse automáticamente en [CHttpFile:: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica del objeto `CHttpConnection` creado por su objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) . El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Vea el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

Se pueden producir excepciones con esta función.

## <a name="see-also"></a>Consulte también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
