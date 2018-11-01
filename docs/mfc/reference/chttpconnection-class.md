---
title: CHttpConnection (clase)
ms.date: 11/04/2016
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 7d11420ca48bfcecbd2534123a36364314b9651c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611008"
---
# <a name="chttpconnection-class"></a>CHttpConnection (clase)

Administra la conexión a un servidor HTTP.

## <a name="syntax"></a>Sintaxis

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Crea un objeto `CHttpConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHttpConnection:: OpenRequest](#openrequest)|Se abre una solicitud HTTP.|

## <a name="remarks"></a>Comentarios

HTTP es uno de los tres protocolos de servidor de Internet implementados por las clases WinInet de MFC.

La clase `CHttpConnection` contiene un constructor y una función de un miembro, [OpenRequest](#openrequest), que administra las conexiones a un servidor con un protocolo HTTP.

Para comunicarse con un servidor HTTP, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, cree un [CHttpConnection](#_mfc_chttpconnection) objeto. No crear nunca un `CHttpConnection` objeto directamente; en su lugar, llame a [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), que crea el `CHttpConnection` de objetos y devuelve un puntero a él.

Para obtener más información sobre cómo `CHttpConnection` funciona con las clases de Internet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre cómo conectarse a los servidores con los otros dos admite protocolos de Internet, gopher y FTP, vea las clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="chttpconnection"></a>  CHttpConnection::CHttpConnection

Se llama a esta función miembro para construir un `CHttpConnection` objeto.

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
Un puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.

*hConnected*<br/>
Identificador de una conexión a Internet.

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor.

*dwContext*<br/>
El identificador de contexto para el `CInternetConnection` objeto. Consulte **comentarios** para obtener más información acerca de *dwContext*.

*nPort*<br/>
El número que identifica el puerto de Internet para esta conexión.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si es NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Un puntero a una cadena terminada en null que especifica la contraseña que se utilizará para iniciar sesión. Si ambos *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL (o una cadena vacía) pero *pstrUserName* no es NULL, se utiliza una contraseña en blanco. En la tabla siguiente describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nombre de usuario se envía al servidor FTP|Contraseña que se envían al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o ""|NULL o ""|"anónimo"|Nombre de correo electrónico del usuario|
|Cadena no nula|NULL o ""|*pstrUserName*|" "|
|Cadena no nula NULL|ERROR|ERROR||
|Cadena no nula|Cadena no nula|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Cualquier combinación de la `INTERNET_FLAG_*` marcas. Consulte la tabla en la **comentarios** sección de [CHttpConnection:: OpenRequest](#openrequest) para obtener una descripción de *dwFlags* valores.

### <a name="remarks"></a>Comentarios

No crear nunca un `CHttpConnection` directamente. En su lugar, se crea un objeto mediante una llamada a [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

##  <a name="openrequest"></a>  CHttpConnection:: OpenRequest

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
Puntero a una cadena que contiene el verbo que se va a utilizar en la solicitud. Si es NULL, se utiliza "GET".

*pstrObjectName*<br/>
Puntero a una cadena que contiene el objeto de destino del verbo especificado. Suele ser un nombre de archivo, un módulo ejecutable o un especificador de búsqueda.

*pstrReferer*<br/>
Un puntero a una cadena que especifica la dirección (URL) del documento desde el que la dirección URL en la solicitud ( *pstrObjectName*) se ha obtenido. Si es NULL, no se especifica ningún encabezado HTTP.

*dwContext*<br/>
Identificador de contexto para la operación `OpenRequest`. Consulte la sección Comentarios para obtener más información acerca de *dwContext*.

*ppstrAcceptTypes*<br/>
Un puntero a una matriz terminada en null de punteros LPCTSTR en cadenas que indica los tipos de contenido aceptados por el cliente. Si *ppstrAcceptTypes* es NULL, los servidores interpretan que el cliente solo acepta documentos de tipo "texto / *" (es decir, solo documentos de texto y no imágenes u otros archivos binarios). El tipo de contenido es equivalente a la variable CONTENT_TYPE de CGI, que identifica el tipo de datos para las consultas que tienen información adjunta, como HTTP POST y PUT.

*pstrVersion*<br/>
Puntero a una cadena que define la versión de HTTP. Si es NULL, se utiliza "HTTP/1.0".

*dwFlags*<br/>
Cualquier combinación de las marcas INTERNET_ FLAG_*. Vea la sección Comentarios para obtener una descripción de posibles *dwFlags* valores.

*nVerb*<br/>
Número asociado al tipo de solicitud HTTP. Puede ser uno de los siguientes:

|Tipo de solicitud HTTP|*nVerb* valor|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CHttpFile](../../mfc/reference/chttpfile-class.md) objeto solicitado.

### <a name="remarks"></a>Comentarios

*dwFlags* puede ser uno de los siguientes:

|Marca de Internet|Descripción|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Fuerza una descarga del archivo, el objeto o el listado de directorio solicitado del servidor de origen, no de la memoria caché.|
|INTERNET_FLAG_DONT_CACHE|No agrega la entidad devuelta a la memoria caché.|
|INTERNET_FLAG_MAKE_PERSISTENT|Agrega la entidad devuelta a la memoria caché como una entidad persistente. Esto significa que las operaciones estándar de limpieza de caché, comprobación de coherencia o recolección de elementos no utilizados no pueden quitar este elemento de la memoria caché.|
|INTERNET_FLAG_SECURE|Usa semántica de transacción segura. Esto se traduce en utilizar SSL/PCT y solo es significativo en solicitudes HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Solo se usa con HTTP, especifica que las redirecciones no se deben administrar automáticamente en [CHttpFile:: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado con esta operación específica de la `CHttpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

Se pueden producir excepciones con esta función.

## <a name="see-also"></a>Vea también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
