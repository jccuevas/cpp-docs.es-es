---
title: CHttpConnection (clase)
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
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351815"
---
# <a name="chttpconnection-class"></a>CHttpConnection (clase)

Administra la conexión a un servidor HTTP.

## <a name="syntax"></a>Sintaxis

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Crea un objeto `CHttpConnection` .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Abre una solicitud HTTP.|

## <a name="remarks"></a>Observaciones

HTTP es uno de los tres protocolos de servidor de Internet implementados por las clases WinInet de MFC.

La `CHttpConnection` clase contiene un constructor y una función miembro, [OpenRequest](#openrequest), que administra las conexiones a un servidor con un protocolo HTTP.

Para comunicarse con un servidor HTTP, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, crear un [CHttpConnection](#chttpconnection) objeto. Nunca se `CHttpConnection` crea un objeto directamente; en su lugar, llame a [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), que crea el `CHttpConnection` objeto y devuelve un puntero a él.

Para obtener más `CHttpConnection` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información acerca de la conexión a servidores mediante los otros dos protocolos de Internet compatibles, gopher y FTP, consulte las clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttpConnection::CHttpConnection

Esta función miembro se `CHttpConnection` llama para construir un objeto.

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

*hConectado*<br/>
Un identificador de una conexión a Internet.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor.

*dwContext*<br/>
Identificador de contexto `CInternetConnection` para el objeto. Para obtener más información acerca de *dwContext*, consulte la sección **Comentarios.**

*Nport*<br/>
El número que identifica el puerto de Internet para esta conexión.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se usará para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL o una cadena vacía, pero *pstrUserName* no es NULL, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword:*

|*pstrUserName*|*pstrPassword*|Nombre de usuario enviado al servidor FTP|Contraseña enviada al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o " "|NULL o " "|"anónimo"|Nombre de correo electrónico del usuario|
|Cadena no NULL|NULL o " "|*pstrUserName*|" "|
|NULL |Cadena no NULL|ERROR|ERROR|
|Cadena no NULL|Cadena no NULL|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Cualquier combinación `INTERNET_FLAG_*` de las banderas. Consulte la tabla de la sección **Comentarios** de [CHttpConnection::OpenRequest](#openrequest) para obtener una descripción de los valores *dwFlags.*

### <a name="remarks"></a>Observaciones

Nunca se `CHttpConnection` crea un directamente. En su lugar, se crea un objeto llamando a [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>CHttpConnection::OpenRequest

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
Puntero a una cadena que contiene el verbo que se va a utilizar en la solicitud. Si se utiliza NULL, "GET".

*pstrObjectName*<br/>
Puntero a una cadena que contiene el objeto de destino del verbo especificado. Esta cadena suele ser un nombre de archivo, un módulo ejecutable o un especificador de búsqueda.

*pstrReferer*<br/>
Puntero a una cadena que especifica la dirección (URL) del documento desde el que se obtuvo la dirección URL de la solicitud (*pstrObjectName*). Si NULL, no se especifica ningún encabezado HTTP.

*dwContext*<br/>
Identificador de contexto para la operación `OpenRequest`. Para obtener más información acerca de *dwContext*, consulte la sección Comentarios.

*ppstrAcceptTypes*<br/>
Puntero a una matriz terminada en null de punteros LPCTSTR a cadenas que indican tipos de contenido aceptados por el cliente. Si *ppstrAcceptTypes* es NULL, los servidores interpretan que el cliente solo acepta documentos de tipo "text/*" (es decir, solo documentos de texto y no imágenes u otros archivos binarios). El tipo de contenido es equivalente a la variable CONTENT_TYPE de CGI, que identifica el tipo de datos para las consultas que tienen información adjunta, como HTTP POST y PUT.

*pstrVersion*<br/>
Puntero a una cadena que define la versión de HTTP. Si se utiliza NULL, se utiliza "HTTP/1.0".

*dwFlags*<br/>
Cualquier combinación de las marcas INTERNET_ FLAG_*. Consulte la sección Comentarios para obtener una descripción de los posibles valores *dwFlags.*

*nVerb*<br/>
Número asociado al tipo de solicitud HTTP. Puede ser uno de los siguientes:

|Tipo de solicitud HTTP|*nValor* de la reverberación|
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

### <a name="remarks"></a>Observaciones

*dwFlags* puede ser uno de los siguientes:

|Marca de Internet|Descripción|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Fuerza una descarga del archivo, el objeto o el listado de directorio solicitado del servidor de origen, no de la memoria caché.|
|INTERNET_FLAG_DONT_CACHE|No agrega la entidad devuelta a la memoria caché.|
|INTERNET_FLAG_MAKE_PERSISTENT|Agrega la entidad devuelta a la memoria caché como una entidad persistente. Esto significa que la limpieza de caché estándar, la comprobación de coherencia o la recolección de elementos no utilizados no pueden quitar este elemento de la memoria caché.|
|INTERNET_FLAG_SECURE|Usa semántica de transacción segura. Se traduce en el uso de SSL/PCT y sólo es significativo en las solicitudes HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Se utiliza solo con HTTP, especifica que las redirecciones no se deben controlar automáticamente en [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado `CHttpConnection` a esta operación específica del objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

Se pueden producir excepciones con esta función.

## <a name="see-also"></a>Consulte también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Clase CHttpFile](../../mfc/reference/chttpfile-class.md)
